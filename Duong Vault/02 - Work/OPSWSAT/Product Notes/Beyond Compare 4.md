```ruby
date_regex = 'released\s+(\w+.\s*\d+,\s*\d+)'
date_content = xml.content.scan(/#{date_regex}/m)
date = WcTime.utils_time_GetFormattedTimeString(date_content[0][0], '%B. %d, %Y', '%m/%d/%Y')
puts "Release date: #{date}"
```

```bash
# all users
Start-Process BCompare-4.4.7.28397.exe -ArgumentList "/SP- /VERYSILENT /NORESTART" -Wait -PassThru

# current user
Start-Process BCompare-4.4.7.28397.exe -ArgumentList "/SP- /VERYSILENT /NORESTART /CURRENTUSER" -Wait -PassThru

```