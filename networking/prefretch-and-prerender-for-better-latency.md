# Pre-fetch and Pre-render for better latency

Firefox, Chrome, Safari and IE have built in API's and extensions onto HTML (not supported across the board) to achieve better networking performance as perceived by a user visiting your web app.

The techniques shown below are examples of what is called *document-aware optimization*: The networking stack is integrated with the document, CSS, and JavaScript parsing pipelines in order to help identify and prioritize critical network assets, dispatch them early, and get the page to an interactive state (i.e. a state that the user feels he/she can interact with the web page and that it's "finished loading" even though it really hasn't) as soon as possible.

1. `<link rel="dns-prefetch" 	href="//hostname_to_resolve.com">`
2. `<link rel="subresource" 	href="/javascript/myapp.js">`
3. `<link rel="prefetch" 		href="/images/big.jpeg">`
4. `<link rel="prerender" 		href="//example.org/next_page.html">`

Basically, you're making intelligent assumptions as to when something should be preloaded based on your users mouse-hovering, page scrolling, eye moving patterns, before the user has actually made a request for that resource, in order to mitigate perceived latency on their part. In order, you are:

1: Pre-resolving a specified hostname.
2: Prefetching a critical resource found later on this same page.
3: Prefetching a resource for this or future navigation.
4: Prerendering a specified page in anticipation of the next user destination.

Hope these kind of techniques give you a new perspective on how you can optimize your web app!