#!/bin/bash

# Multi-domain or single-domain SPF, DKIM, and DMARC Checker

print_usage() {
  echo "Usage:"
  echo "  $0 domain_list.txt <dkim_selector>    # Scan multiple domains from a file"
  echo "  $0 example.com <dkim_selector>        # Scan a single domain"
  exit 1
}

scan_domain() {
  local domain=$1
  local selector=$2

  echo ""
  echo "Domain: $domain"
  echo "-------------------------------------------"

  # === SPF Check ===
  spf_record=$(dig +short TXT "$domain" | grep "v=spf1")
  if [ -n "$spf_record" ]; then
    echo "[+] SPF Record Found:"
    echo "    $spf_record"
    if echo "$spf_record" | grep -qE '^"v=spf1'; then
      echo "[+] SPF syntax looks correct."
    else
      echo "[-] SPF syntax might be incorrect."
    fi
  else
    echo "[-] No SPF Record found."
  fi

  echo ""

  # === DKIM Check ===
  dkim_record=$(dig +short TXT "$selector._domainkey.$domain")
  if [ -n "$dkim_record" ]; then
    echo "[+] DKIM Record Found (selector: $selector):"
    echo "    $dkim_record"
    if echo "$dkim_record" | grep -q "v=DKIM1"; then
      echo "[+] DKIM syntax looks correct."
    else
      echo "[-] DKIM record found but syntax might be incorrect."
    fi
  else
    echo "[-] No DKIM record found for selector $selector."
  fi

  echo ""

  # === DMARC Check ===
  dmarc_record=$(dig +short TXT _dmarc."$domain" | grep "v=DMARC1")
  if [ -n "$dmarc_record" ]; then
    echo "[+] DMARC Record Found:"
    echo "    $dmarc_record"
    if echo "$dmarc_record" | grep -qE '^"v=DMARC1'; then
      echo "[+] DMARC syntax looks correct."
      policy=$(echo "$dmarc_record" | grep -o "p=[a-z]*" | cut -d= -f2)
      echo "[+] DMARC Policy: $policy"
    else
      echo "[-] DMARC syntax might be incorrect."
    fi
  else
    echo "[-] No DMARC Record found."
  fi

  echo "-------------------------------------------"
}

# Entry Point
if [ $# -ne 2 ]; then
  print_usage
fi

input=$1
selector=$2

if [[ -f "$input" ]]; then
  echo "Starting SPF, DKIM, and DMARC scan for domains in: $input"
  echo "==============================================================="
  while read -r domain; do
    [ -z "$domain" ] && continue
    scan_domain "$domain" "$selector"
  done < "$input"
else
  echo "Starting SPF, DKIM, and DMARC scan for single domain: $input"
  echo "==============================================================="
  scan_domain "$input" "$selector"
fi

echo ""
echo "Scan completed."
