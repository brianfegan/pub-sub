pubSub
=======

A native JavaScript implementation of the publish/subscribe pattern.

<p>A pubsub pattern module that can be used to create subscription lists; provides subscribe, unsubscribe, and publish functionality. It uses only native JS and is not dependent on any other libraries.</p>
<p>The subscribe method takes in a subscription name and callback function which fires when the publish method for that subscription is called. It returns a unique id which can be used to unsubscribe from that subscription.</p>
<h2>Usage</h2>
    <script src="pubSub.js"></script>
    <script>
    // Subscribe
    // optional instance parameter lets you retain the value of "this" when callbackFn is fired
    var sub_uid = PubSub.subscribe('subscriptionName', callbackFn, instance);

    // Unsubscribe
    PubSub.unsubscribe('subscriptionName', sub_uid);
    
    // Publish - all subscriber callbackFns fire, with data as an argument
    // If an instance was passed in originally to the subscribe method, 
    // that instance is referenced as "this" in the callback.
    PubSub.publish('subscriptionName', data);
	</script>
	
<h2>Use as a Mixin</h2>
    // Lets say you have an object with methods...
    GenericModuleWithMethods = {
	    init: function(){},
	    doIt: function(){},
	    undoIt: function()
    };
 
    // If this module needs a PubSub pattern, using jQuery...
    $.extend(GenericModuleWithMethods, PubSub);
    GenericModuleWithMethods.subscribe('name', callbackFn);
