# Custom HTML Page Layout Plugin


  This plugin introduces a new Polopoly page layout called "Custom HTML Page Layout". The Page Layout has not pre-defined HTML structure and is intended for use for either building custom Preview Pages for Desk Editor, but can also
  be used for other custom HTML implementations.


  It takes the final part of the path in the content path and inserts the model representation of the content into a stack variables called "article".

  If being used to preview DESK Couchbase content then the following model variables can be used:

    $m.stack.article.contentData.headline.text

    $m.stack.article.contentData.lead.text

    $m.stack.article.contentData.body.text

    $m.stack.article.contentData.byline


   For DESK images , these can be referenced thus:


      #if ($m.stack.article.contentData.images.size() > 0)
        #set ($img = $m.stack.article.contentData.images[0])
        #set ($url=$tool_img.getUrlBuilder($img.content.contentId.contentIdString).width(800).format('3x2').type('jpg').quality(0.6).buildUrl())
        #set ($caption=$img.content.contentData.caption)
      
      <figure >
          <img class="lazyload" data-src="$url" alt="$caption"
                             data-srcset="$url 300w,$url 400w,$url 600w,$url 800w,$url 1000w" data-sizes="auto" />
            <noscript><img src="$url" alt="$caption"></noscript>
      </figure>

      #end

      Access aspects of the image is done like this:

        $img.content.get("atex.Image")
        $img.content.get("atex.ImageEditInfo")
        
   For more details on how to use Velocity see http://support.atex.com/confluence/display/GONGMaster/Velocity+utilities
   
  # How to create an Article Preview page
  
  1. Navigate to your chosen Article page as a template. 
  2. Save the source of the page to HTML
  3. Pretty-ify the HTML to make it easier to read.
  4. Break up the HTML into 3 sections, header, body & footer - this will make maintenance simpler.
  5. See above to insert placeholders in the HTML to represent Preview article. Replace the actual values in the sample with the placeholder variables.
 
  
  
