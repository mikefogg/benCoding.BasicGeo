<h1>benCoding.basicGeo</h1>
 
Welcome to the benCoding.basicGeo Titanium project

<h2>basicGeo for iOS</h2>

The benCoding.basicGeo module provides enhanced geo location functionality over the core Titanium framework. For example you can access the native platform reverse geo decoders, or use the built in distance calculations methods.

<h2>Before you start</h2>
* You need Titanium 1.8.2 or greater.
* This module will only work with iOS 5 or great.  

<h2>Setup</h2>

* Download the latest release from the [dist folder](https://github.com/benbahrenburg/benCoding.BasicGeo/tree/master/IOS/basicGeo/dist) or you can build it yourself 
* Install the bencoding.basicGeo module. If you need help here is a "How To" [guide](https://wiki.appcelerator.org/display/guides/Configuring+Apps+to+Use+Modules). 
* You can now use the module via the commonJS require method, example shown below.

<pre><code>
//Add the core module into your project
var geo = require('bencoding.basicgeo');

</code></pre>

Now we have the module installed and avoid in our project we can start to use the components, see the feature guide below for details.

<h2>Features</h2>

<h3>Availability</h3>
Content pending

<h3>CurrentGeolocation</h3>
Content pending

<h3>Geocoder</h3>

<h4>reverseGeocoder</h4>

Tries to resolve a location to an address.

The callback receives a results object. If the request is successful, the object includes one or more addresses that are possible matches for the requested coordinates.

Parameters:
* latitude : Number
* longitude : Number
* callback : Function to invoke on success or failure.


Both parameters are required.

<pre><code>

//Add the core module into your project
var geo = require('bencoding.basicgeo');

function reverseGeoCallback(e){
	Ti.API.info("Did it work? " + e.success);
	if(e.success){
		Ti.API.info("This is the number of places found, it can return many depending on your search");
		Ti.API.info("Places found = " + e.placeCount);
		for (var iLoop=0;iLoop<e.placeCount;iLoop++){
			Ti.API.info("Showing Place At Index " + iLoop);
			Ti.API.info(JSON.stringify(e.places[iLoop]));
		}		
	}	

	var test = JSON.stringify(e);
	Ti.API.info("Forward Results stringified" + test);
};

Ti.API.info("Now let's check out the GeoCoders")
var geoCoder = geo.createGeocoder();

Ti.API.info("Now let's do some forward Geo and lookup the address for Appcelerator HQ");
var address="440 N. Bernardo Avenue Mountain View, CA";

Ti.API.info("Let's now try to do a reverse Geo lookup using the Time Square coordinates");
Ti.API.info("Pass in our coordinates and callback then wait...");
geoCoder.reverseGeocoder(40.75773,-73.985708,reverseGeoCallback);

</code></pre>

<h4>forwardGeocoder</h4>

Resolves an address to a location.
Parameters:
* Address : String
* callback : Function to invoke on success or failure.

Both parameters are required.

<pre><code>
//Add the core module into your project
var geo = require('bencoding.basicgeo');

function forwardGeoCallback(e){
	Ti.API.info("Did it work? " + e.success);
	if(e.success){
		Ti.API.info("This is the number of places found, it can return many depending on your search");
		Ti.API.info("Places found = " + e.placeCount);
		for (var iLoop=0;iLoop<e.placeCount;iLoop++){
			Ti.API.info("Showing Place At Index " + iLoop);
			Ti.API.info(JSON.stringify(e.places[iLoop]));
		}		
	}	

	var test = JSON.stringify(e);
	Ti.API.info("Forward Results stringified" + test);
};

Ti.API.info("Now let's check out the GeoCoders")
var geoCoder = geo.createGeocoder();

Ti.API.info("Now let's do some forward Geo and lookup the address for Appcelerator HQ");
var address="440 N. Bernardo Avenue Mountain View, CA";

Ti.API.info("We call the forward Geocoder providing an address and callback");
Ti.API.info("Now we wait for the lookup");
geoCoder.forwardGeocoder(address,forwardGeoCallback);

</code></pre>

<h3>SignificantChange</h3>
Content pending

<h3>LocationMonitor</h3>
Content pending

<h3>Telephony</h3>

The Telephony class provides access to the geo location methods related to your SIM card.

Below shows how to use this class to obtain the ISO country code for the user’s cellular service provider. This is the carrier on the SIM.  Here is a listing of ISO codes [wikipedia](http://en.wikipedia.org/wiki/ISO_3166-1)

<pre><code>
//Add the core module into your project
var geo = require('bencoding.basicgeo');
//Create the Telephony object
var geoTelephony = geo.createTelephony();
//Return the country code associated with your SIM
Ti.API.info("Your SIM Country Code is " + geoTelephony.mobileCountryCode());
</code></pre>


<h3>Helpers</h3>
Content pending

<h2>Examples</h2>

Please check the [example](https://github.com/benbahrenburg/benCoding.BasicGeo/tree/master/IOS/basicGeo/example) for samples on how to call the different functions contained within the module.

The examples for this project are still a work in progress, until I can completely document the project please contact me on twitter if you have a specific question.

<h2>Licensing & Support</h2>

This project is licensed under the OSI approved Apache Public License (version 2). For details please see the license associated with each project.

Developed by [Ben Bahrenburg](http://bahrenburgs.com) available on twitter [@benCoding](http://twitter.com/benCoding)

<h2>Contributing</h2>

The benCoding.basicGeo is a open source project.  Please help us by contributing to documentation, reporting bugs, forking the code to add features or make bug fixes or promoting on twitter, etc.

<h2>Learn More</h2>

<h3>Twitter</h3>

Please consider following the [@benCoding Twitter](http://www.twitter.com/benCoding) for updates and more about Titanium.

<h3>Blog</h3>

For module updates, Titanium tutorials and more please check out my blog at [benCoding.Com](http://benCoding.com). 