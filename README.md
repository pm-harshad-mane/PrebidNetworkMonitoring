# Prebid Network Monitoring

- No bucketing logic, logging absolute values to StatHat
- Removed Google from monitoring as there are many calls to Google on the page
- The code will run 2000 ms after auction end, it is configurable using `executionDelayInMs`
- Using `testGroupPercentage` you can mention how many times in percentage the code should run, `10` value means only 10% times we will monitor
- Using `prebidNamespace` you can change the namespace that the publisher is using to run Prebid auctions. If publisher has IDHUB (under owpbjs namespace) and own Prebid setup(under pbjs namespace) then we should mention `pbjs` as the value
- The StatHat keys generated with code will differ from the keys for Chrome Extension, this code adds a prefix 'PWT', cstomizable with `statHatPrefix`
- Using `bidders` you can specify which bidders/domains to monitor
- In this code the value for the Country parameter is set with `navigator.language` as this code can't have an input and Country detection in JS comes with an additional cost. The value for US country will be something like `en-US` for an englishe speaking person. We may want to change this after iinitial run.
- As page can run multiple auctions, the code takes care of not gathering stats for the network calls made in previous auction

# Good To Have
- we can add bid/no-bid signal in the key name as when biddder has bid-response the response size will be larger than the no-bid response.
