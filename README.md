 name: gitartwork from a contribution graph
 on: 
   push:
   schedule:
     - cron: '* */24 * * *'
 jobs:
   build:
     name: Make gitartwork SVG
     runs-on: ubuntu-latest
     steps:
       - uses: actions/checkout@v3
       - uses: jasineri/gitartwork@v1
         with:
            # Use this username's contribution graph  
            user_name: jasineri
            # Text on contribution graph 
            text: JASINERI
       - uses: jasineri/simple-push-action@v1
