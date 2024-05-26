![00](https://github.com/0x3f3c/Bugbounty-subs/assets/154844497/c41426a8-826c-4d74-a321-00bfc67c55a7)

**HackerOne**

### Get all subs



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/hackerone.json" | jq -r '.[].relationships.structured_scopes.data[].attributes.asset_identifier' | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

### Get subs using orgname



[![image](https://user-images.githubusercontent.com/72344025/234682490-3c9b4f9d-aad0-4dce-9277-5f7b7b87a0b5.png)](https://user-images.githubusercontent.com/72344025/234682490-3c9b4f9d-aad0-4dce-9277-5f7b7b87a0b5.png)

```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/hackerone.json" | jq -r '.[] | select(.attributes.submission_state=="open" and .attributes.offers_bounties==true and .attributes.name=="Informatica") | .relationships.structured_scopes.data[].attributes.asset_identifier' | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | sed 's/http[s]*:\/\/\|www.//g' | unew -p
```

### Get all wildcard in_scope subs



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/hackerone.json" | jq -r '.[] | select(.attributes.submission_state=="open" and .attributes.offers_bounties==true) | .relationships.structured_scopes.data[].attributes | select(.eligible_for_bounty==true) | .asset_identifier' | tr "," "\n" | sed 's/http[s]*:\/\/\|www.//g' | sed 's/\s//g' | grep "^*" | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | unew -p
```

### Get all wildcard in_scope subs using orgname



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/hackerone.json" | jq -r '.[] | select(.attributes.name=="Uber") | .relationships.structured_scopes.data[].attributes | select(.eligible_for_bounty==true) | .asset_identifier' | grep "*" | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

**BugCrowd**

### Get all subs



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/bugcrowd.json" | jq -r '.[].target_groups[].targets[].name' | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

### Get in_scope and out_scope subs using program_url



[![image](https://user-images.githubusercontent.com/72344025/234680472-6d7da018-f325-4812-aabf-9a5e414cdeef.png)](https://user-images.githubusercontent.com/72344025/234680472-6d7da018-f325-4812-aabf-9a5e414cdeef.png)

```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/bugcrowd.json" | jq -r '.[] | select(.program_url=="/dell-com") | .target_groups[].targets[].name' | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

### Get in_scope subs using program_url



[![image](https://user-images.githubusercontent.com/72344025/234680651-5ce28fa8-71e6-414f-81d0-7f5f03a33d15.png)](https://user-images.githubusercontent.com/72344025/234680651-5ce28fa8-71e6-414f-81d0-7f5f03a33d15.png)

```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/bugcrowd.json" | jq -r '.[] | select(.briefUrl=="/ciscomeraki") | .target_groups[] | select(.in_scope==true) | .targets[] | "\(.name)\n\(.uri)"' | egrep -v "null" | tr "," "\n" | sed 's/http[s]*:\/\/\|www.//g' | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | sed 's/\s//g' | unew -p
```

### Get all wildcard in_scope subs



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/bugcrowd.json" | jq -r '.[] | .target_groups[] | select(.in_scope==true) | .targets[].name' | grep "*." | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

### Get all wildcard in_scope subs using program_url



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/bugcrowd.json" | jq -r '.[] | select(.program_url=="/tesla") | .target_groups[] | select(.in_scope==true) | .targets[].name' | grep "*." | anew
```

### Get all wildcard in_scope Reward subs



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/bugcrowd.json" | jq -r '.[] | select(.license_key=="bug_bounty") | .target_groups[] | select(.in_scope==true) | .targets[].name' | grep "*." | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

### Get all wildcard in_scope Reward subs using program_url



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/bugcrowd.json" | jq -r '.[] | select(.program_url=="/rmit-university-vdp-pro") | select(.license_key=="bug_bounty") | .target_groups[] | select(.in_scope==true) | .targets[].name' | grep "*." | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

**Intigriti**

### Get all subs



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/intigriti.json" | jq -r '.[].domains[].endpoint' | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

### Get subs using program handle name



[![image](https://user-images.githubusercontent.com/72344025/234679727-fef11a91-c8f6-4623-b176-e92cdf5b027d.png)](https://user-images.githubusercontent.com/72344025/234679727-fef11a91-c8f6-4623-b176-e92cdf5b027d.png)

```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/intigriti.json" | jq -r '.[] | select(.handle=="upholdcom") | .domains[].endpoint' | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

### Get all wildcard in_scope subs



```shell
curl -s "https://raw.githubusercontent.com/Osb0rn3/bugbounty-targets/main/programs/intigriti.json" | jq -r '.[].domains[].endpoint' | grep "^*" | grep -Eo '[a-zA-Z0-9]+([.-][a-zA-Z0-9]+)*\.[a-zA-Z]{2,}' | anew
```

## Support and Questions
