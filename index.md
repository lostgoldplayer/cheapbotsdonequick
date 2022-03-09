Creating image bots using SVG and Tracery

To create images we need to use SVG. CBDQ takes a screenshot of the SVG image and creates a PNG which it uploads to Twitter.

Tracery with SVG will look like this: "origin": "your usual tweet text {svg <svg>YOUR SVG CODE</svg>}". Pretty much any SVG will work.

You can paste the following examples into CBDQ and they should just work.
The most basic example:

    { "origin": "Here is some SVG: {svg <svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" width=\"1024\" height=\"512\"></svg>}" }

Things to note: you need to escape any double quotes (so " becomes \") and you need to define the width and height of the image. I think you can use any size you like, but I usually use 1024x512 pixels as it shows up complete and uncropped in the Twitter and Tweetdeck timelines.
Embed an image

To include an image use the <image> SVG tag. You don't need to define the width or height but it's helpful. You can host the images anywhere - I use Dropbox a lot.

    { "origin": "any text / link you like {svg <svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" width=\"width\" height=\"height\"><image width=\"width\" height=\"height\" xlink:href=\"path to your image\" /></svg>}" }

Here's an example. I've set the width and height of both the SVG object and the image to 512x512.

    { "origin": "nonsensical infographics http://www.chadhagen.com/nonsensical-infographics {svg <svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" width=\"512\" height=\"512\"><image width=\"512\" height=\"512\" xlink:href=\"https://pbs.twimg.com/media/Ch8jRkUWwAAaSlE.jpg:large\" /></svg>}" }

Here's what that looks like:

It's all Tracery, so you can put symbols anywhere you like. This example loads a randomly selected image:

    { "origin": "over the garden wall {svg <svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" width=\"540\" height=\"380\"><image width=\"540\" height=\"380\" xlink:href=\"#image#\" /></svg>}", "image": ["https://typeset-beta.imgix.net/rehost%2F2016%2F9%2F13%2F99d6595b-3e04-44f1-9fc4-fde9852eb51f.jpg", "http://deadshirt.net/wp-content/uploads/2014/11/1.jpg"] }

Here's what that looks like:

Adding text to your image

To add text use the <text> SVG tag.

<text x=\"256\" y=\"300\" font-size=\"30\" text-anchor=\"middle\">plain text</text>

    { "origin": "plain text {svg <svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" width=\"500\" height=\"391\"><image width=\"500\" height=\"391\" xlink:href=\"https://s-media-cache-ak0.pinimg.com/736x/ae/fb/9a/aefb9a99eab8f0eebdb0c599a78b1b75.jpg\" /><text x=\"256\" y=\"300\" font-size=\"30\" text-anchor=\"middle\">WHAT IS GOING ON HERE???</text></svg>}" }

Play around with the x and y values to move the text around. Setting text-anchor="middle" means the text is centred.

But we can do better and style the text.

    { "origin": "nicer text {svg <svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" width=\"500\" height=\"391\"><image width=\"500\" height=\"391\" xlink:href=\"https://s-media-cache-ak0.pinimg.com/736x/ae/fb/9a/aefb9a99eab8f0eebdb0c599a78b1b75.jpg\" /><text x=\"256\" y=\"300\" font-size=\"30\" stroke=\"black\" stroke-width=\"1\" fill=\"white\" text-anchor=\"middle\" style=\"font-family: Impact\">WHAT IS GOING ON HERE???</text></svg>}" }

We're limited to the fonts installed on the computer that runs CBDQ, which isn't much. Happily we can embed webfonts (you can choose from about a million here https://fonts.google.com/)

    { "origin": "pretty text using a webfont {svg <svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" width=\"500\" height=\"391\"><image width=\"500\" height=\"391\" xlink:href=\"https://s-media-cache-ak0.pinimg.com/736x/ae/fb/9a/aefb9a99eab8f0eebdb0c599a78b1b75.jpg\" /><text x=\"256\" y=\"300\" font-family=\"Luckiest Guy\" font-size=\"30\" stroke=\"black\" stroke-width=\"1\" fill=\"white\" text-anchor=\"middle\" style=\"font-family:'Luckiest Guy'\">WHAT IS GOING ON HERE???</text><style type=\"text/css\">@import url(https://fonts.googleapis.com/css?family=Luckiest+Guy);</style></svg>}" }

Much better!
Motivational poster bot

Put it all together and we can create a fake motivational poster bot. This one loads a random image, creates a nonsense sentence, and uses the same text in the tweet as well as in the image (using Tracery variables)

    { "origin" : ["#statement_with_image#"], "statement_with_image" : ["[statement:#statement.capitalize#] #statement# {svg <svg xmlns=\"http://www.w3.org/2000/svg\" xmlns:xlink=\"http://www.w3.org/1999/xlink\" version=\"1.1\" width=\"890\" height=\"525\" style=\"position: relative;\"><image x=\"0\" y=\"0\" width=\"890\" height=\"525\" xlink:href=\"#image#\" /><foreignObject x=\"0\" y=\"0\" width=\"890\" height=\"525\"><p xmlns=\"http://www.w3.org/1999/xhtml\" style=\"padding: 2%; width: 90%; font-size:80px; line-height:1.2; color:rgba(255, 255, 255, 1); font-family:'Luckiest Guy'; text-align:center; 0; position: absolute; bottom: 0px; background-color: rgba(0, 0, 0, 0.5); margin:5%;\">#statement#</p></foreignObject><style type=\"text/css\">@import url(https://fonts.googleapis.com/css?family=Luckiest+Guy);</style></svg>}"], "googlefont" : ["Luckiest Guy"], "image" : ["https://static.pexels.com/photos/6546/sky-night-space-trees-large.jpeg", "https://static.pexels.com/photos/94847/pexels-photo-94847-large.jpeg", "https://static.pexels.com/photos/96377/pexels-photo-96377-large.jpeg", "https://static.pexels.com/photos/96414/pexels-photo-96414-large.jpeg", "https://static.pexels.com/photos/96375/pexels-photo-96375-large.jpeg", "https://static.pexels.com/photos/95632/pexels-photo-95632-large.jpeg"], "statement": ["wake up and #sense# the #thing#"], "sense" : ["smell", "enjoy", "taste"], "thing" : ["coffee", "tea", "marmite", "peanut butter", "milk", "orange juice", "granola"] }

Coming soon

    overlaying images on top of each other

    eg. @sadkeanubot, @jakerunningbot

    using SVG filters to modify images

    eg. @badphotoquality, @computerzooom

    using javascript to modify SVG content

    eg. @botlifemagazine, @sleeps_xmas
