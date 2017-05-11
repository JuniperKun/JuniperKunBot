# JuniperKunBot

console.log("Get ready for bot time");

var Twit = require('twit')

var T = new Twit({
  consumer_key:         '2MhFeYAODOcebhxoZlpbWKdSn',
  consumer_secret:      '1qC9tE68kMo33dwYMV4sfYpRJpivbg5d6vOWBZSxs8qJa6jYVV',
  access_token:         '861935685703434241-clAcIMvv6qsGXVVULjFog7nLQVix7PD',
  access_token_secret:  '1fChxY1TPnO4V1mHKhgLOc3ruJkQc0T6qao6jDWR2ofMX',
  //timeout_ms:           60*1000,  // optional HTTP request timeout to apply to all requests.
})
// setInterval(tweetIt, 1000*60*60*24); 

var stream = T.stream('user');

stream.on('follow', followed);

function followed(eventMsg) {
	var name = eventMsg.source.name;
	var screenName.source.screen_name;
	tweetIt('@' + screenName + 'am I alive?');
}

 
function tweetIt(txt) {
	var tweet = {
		status: txt
	}

	T.post('statuses/update', tweet, tweeted);

	function tweeted(err, data, response) {
		if(err){
			console.log('something went wrong')
		} else {
			console.log('OMFG it worked')
		}
	}
}

/*function tweetIt() {
	T.get('search/tweets', 

		{
		q: 'poop', 
		count: 1 
		}, 

		function(err, data, response) {
  			var tweets = data.statuses;
  			for ( var i = 0; i < tweets.length; i++){
  				console.log(tweets[i].text);
  				T.post('statuses/update', { status: tweets[i].text }, function(err, data, response) {
  					console.log(data)
  					if (err) {
  						console.log('something went wrong!')
  					}else{
  						console.log('OMG it worked!')
  					}
				})
  			}
		}
	)
}*/
 


