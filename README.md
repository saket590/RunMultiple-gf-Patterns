### RunMultiple-gf-Patterns
One liner command to run the gf patterns. gf is a wonderful tool developed by the famous hacker Tomnomnom (Ref :https://github.com/tomnomnom/gf)
Most of the time, while using gf tool, people generally use single commands such as 
`cat urls.txt | gf xss`

or

`cat urls.txt | gf sqli`  and so on..


To reduce the time and grep for multiple patterns at once, such as xss,sqli,lfi, etc, the below command can be used to grep all the patterns and provide output in separate files, which can be then analysed. 
```
patterns=("Allin1gf" "or" "allparam" "parsers" "api-keys" "paypal-token_secrets" "asymmetric-keys_secrets" 
          "php-callbacks" "php-codeexec" "aws-keys" "php-commandexec" "php-curl" "php-errors" 
          "php-informationdisclosure" "php-open-filesystem-handler" "php-read-filesystem" 
          "php-serialized" "php-sinks" "php-sources" "php-write-filesystem" "picatic-keys_secrets" 
          "rce-2" "rce" "redirect" "s3-buckets" "sec" "secret-ext" "secrets" "secret-urls" 
          "serial" "servers" "slack-token" "slack-token_secrets" "slack-webhook" 
          "slack-webhook_secrets" "sqli-error" "sqli" "ssrf" "ssti" "strings" "swearwords" 
          "takeovers" "truffle" "twilio-key" "twilio-keys_secrets" "typos" "upload-fields" 
          "urlparams" "urls" "urls_params" "xml" "xpath" "xss" "xxe")

for pattern in "${patterns[@]}"; do
  echo "Processing pattern: $pattern"
  if cat urls.txt | gf "$pattern" > "gf${pattern}.txt"; then
    echo "Successfully processed $pattern."
  else
    echo "Error processing $pattern. Skipping..." >> error.log
  fi
done

```

**Example Outputs:**
If successful:\
Files like gfAllin1gf.txt, gfxss.txt, etc., will be created with the results.
Console will display: Successfully processed Allin1gf.

If an error occurs:\
An entry like Error processing Allin1gf. Skipping... will be added to error.log.
The script will move to the next pattern without interruption.


Ensure the required JSON patterns are present under the ~/.gf directory. These can be obtained from:

https://github.com/emadshanab/Gf-Patterns-Collection  (Contains various links for patterns)\
https://github.com/coffinxp/gFpattren  \

A big thanks to these hackers for providing these useful patterns.
