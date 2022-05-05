---
title       : "Codebase"
description : "A page with my code samples."
tags        : [ code, "syntax highlighting" ]
toc         : true
date: 2021-12-11T19:52:48+02:00
lastmod: 2021-12-11T19:52:48+02:00
---

<!-- To add videos  

To show videos, uncomment this and add a video folder with the file in it to the directory of the page

{{< gifoid "video_name" "VideoDescription" border >}} -->


## This is what I had to do every single time I make an update before having workflow:
```
# remove previous publication
rm -rf public
mkdir public

# clone gh-pages branch from the local repo into a repo located within "public"
git clone .git --branch gh-pages public
  
# generate
hugo
  
# commit the changes in the clone and push them back to the local gh-pages branch    
cd public 
git add --all
git commit -m "Publishing to gh-pages" 
git push origin gh-pages
git remote add upstream https://github.com/cs-ej4104-2021/darkhan-s-project.git
git push upstream gh-pages
```

## My deploy-worflow.yml file for automatic deployment

```yml

name: Build and deploy GitHub pages with Hugo

on:
  push:
    branches:
      - main
      - master
  pull_request:

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: '0.89.4'
          extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_branch: gh-pages
          publish_dir: ./public
```

## Now I only wait until the build is complete
{{< figure "output.jpg" "Deployment output example" "border" >}}


## My config.toml file (main file for Hugo website configuration)

```toml
baseURL = "https://darkhan-s.github.io/personal-website"
#baseURL = "/"
languageCode = "en"
title = "Saidnassimov Darkhan"
theme = "color-your-world"

# Used only in the RSS file
copyright = "Copyright © 2022, Darkhan Saidnassimov; All rights reserved."

enableEmoji = true
enableInlineShortcodes = true

paginate = 3


# TEST
# Netlify _headers
[outputs]
  home    = [ "HTML", "RSS", "HEADERS" ]
  section = [ "HTML", "RSS" ]

[mediaTypes."text/netlify"]
  suffixes  = [ "" ]
  delimiter = ""

[outputFormats.HEADERS]
  mediaType       = "text/netlify"
  baseName        = "_headers"
  isPlainText     = true
  notAlternative  = true



[markup.highlight]
  # To make use of the custom Chroma, this should be false
  # The default is true
  noClasses = false



[params]
  
  # Site description
  description = "DevOps Project"
  
  # Author
  author      = "Saidnassimov Darkhan"
  authorDesc  = "Another Aalto student"
  
  # Footer text
  # Each value will become a paragraph
  # Keep it as an array
  footerText = [ "Generated with [Hugo](https://gohugo.io) using the [Color Your World](https://gitlab.com/rmaguiar/hugo-theme-color-your-world) theme." ]

  
  # Site cover, for Open Graph, Twitter Cards and Schema.org
  # It will be used if the current page doesn't have a image cover
  # File will be picked from the "assets" directory
  # Comment the lines if you don't want to use it
  #cover     = "img/cover.jpg"
  #coverAlt  = "A placeholder that doesn't deserve to be described."
  
  # Shows a message in the footer about JavaScript being disabled
  # The default is false
  hasNoscriptNotice = true
  
  # Default path for images in posts
  # ie.: "content/some-post/img"
  # Can also be set PER PAGE
  # It can be used to reduce repetition
  # There's no default value
  imgPath = "img"
  
  # Default classes for markup image 
  # Modifies the default behavior of images placed via markdown
  # Can also be set PER PAGE via front matter
  # Available classes are: border and borderless
  # There's no default value
  markupImgClass = ""
  
  # This will append a separator (of your choice) along the site title to your <title>
  # ie.: | ❚ - – — • ⚫ 
  # You can disabled it PER PAGE by using "disableTitleSeparator" at front
  # matter or disable it entirely by commenting the line below
  titleSeparator = "|"
  
  
  # Contact form shortcode
  [params.contact]
  
    # formspree.io Form ID
    formspreeFormId = "example"
    
    # Autocomplete [on/off] and min character length for message
    autoComplete      = false # Default is false
    messageMinLength  = 140   # Default is 140
    
    # Subject
    # You can set a single value below (and it will cease to be a dropdown),
    # BUT KEEP IT AS AN ARRAY
    # It can also be disabled entirely (and it will turn into a text field)
    #subject = [ 'Just saying "hi"', "I know what you did last winter", "... Is that a sloth?", "お前はもう死んでいる。" ]

    # Text placeholders. As usual, comment the lines if you don't want use them
    # The "subject" below will only be used if the "subject" above doesn't exist (ie.: commented/deleted)
    [params.contact.placeholder]
      name    = "Your name"
      email   = "your@email.com"
      subject = 'Subject topic'
      message = "Enter your message here.."


  [params.search]
  
    # Enable search form (at the post list)
    # The default value is false
    enable = true
  
    # Limit search results
    # The default value is 30
    maxResults = 15
    
    # Limit seach field input and pattern matching
    minLength = 2   # Default is 3
    maxLength = 42  # Default is 32
    
    # Optional placeholder for search field
    placeholder = "Start typing..."
    

  [params.style]
  
    # Dark mode as default
    # User preferences (site/system settings) will still have priority over it
    # The default is false
    isDark = true

    # Disable the use of system settings (prefers-color-scheme)
    # The default is false
    ignoreSystemSettings = true

    # Accent colors for dark and light mode respectively
    darkAccent   = "#1dbc91" # Default is "#1dbc91"
    lightAccent  = "#1f676b" # Default is "#1f676b"

    # More colors, pick as many as you want (not really sure if there's a limit)
    # Apparently these may not show up on every modern browser (ie. Firefox)
    # There's no default value. Used here just as example
    presets = [ "#225670", "#dd587c", "#902b37", "#f3a530", "#754e85", "#7fc121", "#a8314a", "#ff7433", "#3e6728", "#c063bd" ]

    # Use an icon or text for footnote return links
    # The default is false
    hasIconAsFootnoteReturnLink = true
    
    # For the social shortcode
    # Use flexbox (with flex-grow) or grid (equal width)
    # The default is false
    socialIsFlex = true
    
    # Keep anchor links hidden until it's focused/hovered
    # The default is false
    hideAnchors = true
    
    # To make use of the custom Chroma, this should be true
    # and "noClasses" (at markup.highlight) should be false
    # The default is true
    useCustomChroma = true

    # CSS animation transition when changing colors
    # The default is ".5s ease"
    changeTransition = ".3s ease"
    
    
  # For a simple 404
  [params.notFound]
    title         = "Page not found"
    description   = "This page was not found."
    paragraph     = "Nothing to see here, buddy."
    
  [params.social.centralized]
    github        = [ "darkhan-s" ]
    linkedin      = [ "dsaidnassimov" ]
    
    # The "entry" here IS important. It's used to load the data.

  [params.social.decentralized]
  
    [params.social.decentralized.element]
      
    [params.social.decentralized.matrix]
     
    # The "entry" here ISN'T important. It's used for nothing.
    
    
[privacy]


[services]


[languages]

  [languages.en]
  
    languageName = "English"

    [languages.en.menu]

      [[languages.en.menu.main]]
        name = "About me"
        weight = 1
        url = "https://darkhan-s.github.io/personal-website"
        #url = "/"

      [[languages.en.menu.main]]
        name = "Posts"
        weight = 2
        url = "posts/"
      
```