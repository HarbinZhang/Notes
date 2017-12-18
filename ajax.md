


# AJAX
### Asynchronous JavaScript And XML request.
- Asynchronous  
refers to the fact that the request doesn't block other events from happening.
- MapAPI
```
    var mapApi = "http://maps.googleapis.com/maps/api/streetview?size=600x300&location=";
    mapApi += street + ', ' + city;
    $body.append('<img class="bgimg" src="' + mapApi + '"">');

```
- NYAPI
```
    var NYAPIKey = "fe99ba23b0fb432ca1043de6c66ef20b";
    var NYurl = "https://api.nytimes.com/svc/search/v2/articlesearch.json";
    NYurl += '?' + $.param({
    	'q':street + ' ' + city,
    	'api-key': NYAPIKey
    });


    $.ajax({
    	url:NYurl,
    	method: 'GET',
    }).done(function(data){

    	var items = [];
    	// console.log(data.response.docs[0]);
    	$.each(data.response.docs, function(key, value){
    		// $("<li>").attr("").

    		$nytElem.append($("<li>").attr("id", value._id)
    			.append($("<a>").attr("href", value.web_url).text(value.headline.main))
    			.append($("<p>").text(value.snippet)));
    	});
    }).fail(function(err){
    	throw err;
    });
```
- wikiAPI (COR)
CORS (cross-origin resource sharing)
There is no error handling function for jsonp. So use timeout here.
```
    var wikiUrl = 'http://en.wikipedia.org/w/api.php?action=opensearch&search='+
    		city + '&format=json&callback=wikiCallback';

    var wikiRequestTimeout = setTimeout(function(){
    	$wikiElem.text("failed to get wikipedia resources");
    }, 8000);
    // Wiki
    $.ajax({
    	url:wikiUrl,
    	dataType:"jsonp",
    	// jsonp: "callback",
    	success:function(response){
    		// console.log(response);

    		// handle

    		// after handling done 
    		clearTimeout(wikiRequestTimeout);
    	}
    });
```
