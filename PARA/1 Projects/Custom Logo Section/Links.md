- YouTube Video on the Freeform (FF) Designer - https://www.youtube.com/watch?v=Xqzy0lG9HHk
- PulseId documentation - 
	- https://webapi.pulseidconnect.com
	- https://webapi.pulseidconnect.com/Documentation?utm_source=chatgpt.com
	- https://tajimaeurope.com/en/pulse-software-solutions/automation
	- https://tajimaeurope.com/en/pulse-software-solutions/embroidery-software-tajima-software-dg16-pulse/
	- GitHub PulseIDJS - https://github.com/pulsemicro/PulseIDJS?utm_source=chatgpt.com
- API Details
	- API URL:  `https://rockbottom.pulseidconnect.com/api`
	- API KEY: `pulseRockBottomGolf`
	- Company: PersonalizeYourGear
- - curl testing
	- 
	  ```curl
curl -v "http://localhost:3000/pulseid/api/Designer/GetProduct?variantId=02CAL24FWYC11111111WHA01&originalSize=true&showBackgroundOnZoom=true&sku=02CAL24FWYC11111111WHA01" \
  -H "apiKey: pulseRockBottomGolf" \
  -H "company: PersonalizeYourGear"
```

```curl
curl -v "http://localhost:3000/pulseid/api/api/Designer/GetProduct?variantId=02CAL24FWYC11111111WHA01&originalSize=true&showBackgroundOnZoom=true&sku=02CAL24FWYC11111111WHA01" \
  -H "apiKey: pulseRockBottomGolf" \
  -H "company: PersonalizeYourGear"Understanding_CORS_and_Proxy
```

```curl
curl -v "http://localhost:3000/pulseid/api/api/Designer/GetProduct" \
  -H "apiKey: pulseRockBottomGolf" \
  -H "company: PersonalizeYourGear"
```

- Template Design demo
	- Sample Product URL: https://rockbottomgolf2.com/purple-t-shirt/
	- PulseID Admin URL: m://stagerockbottom.pulseidconnect.com/
		- Username: RockBottomGolfTest
		- Password: RockBottomGolfTest
- Netlify site: https://app.netlify.com
- Original Netlify personal URL - https://bejewelled-phoenix-0ff664.netlify.app
- Rename Netlify URL (Project): https://rbg-custom-pulseid-widget
- URL to Netlify Function: `https://rbg-custom-pulseid-widget.netlify.app/.netlify/functions/pulseid-proxy`
- `https://rbg-custom-pulseid-widget.netlify.app/.netlify/functions/pulseid-proxy?path=api%2Fapi%2FDesigner%2FGetProduct&variantId=02CAL24FWYC11111111WHA01&originalSize=true&showBackgroundOnZoom=true&sku=02CAL24FWYC11111111WHA01`

-  New template designer - https://rockbottomgolf2.com/bag-boy-golf-chiller-cart-bag/?showHidden=true&ctk=5a218f91-9543-4343-b58a-66771b04e508

- GolfBags
	- `https://www.golfbags.com`
- GolfBags Demo
	- `https://golf-bags.mybigcommerce.com`

`https://golf-bags.mybigcommerce.com/bag-boy-golf-revolver-xp-cart-bag/`

`https://rbg-custom-pulseid-widget.netlify.app/?variantid=02BBYCHILCT11111111BBS01`