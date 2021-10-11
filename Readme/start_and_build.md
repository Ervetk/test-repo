# Setting up simple build proccess
[Udemy video](https://www.udemy.com/course/advanced-css-and-sass/learn/lecture/8274568#overview)
1) Veendu, et oleks olemas `package.json` fail. Seal sees oluline info, et mida vaja installida npm-ga.
1)  `npm i`
- see installib kõik seosed ja node moodulid (node mooduleid ei tarvitse siin VS Codes kohe näidata)
- Kui json script on olemas failis `package.json` siis selleks, et käivitaa SASS Compiler ja Live Server kasuta käsklust:
`"start": "npm-run-all --parallel devserver watch:sass",`
2) `npm run start` 
- käivitab korraga `devserver` ja `watch:sass`--> See script:
3) `npm run build:css` sellega teeb css lõppfaili

```json
{
	"name": "swissotel_landing_1",
	"version": "1.0.0",
	"description": "Easy landingpage",
	"main": "index.js",
	// UUE PROJEKTI JAOKS COPY SEE ALATES SIIT -->
	"scripts": {
		"watch:sass": "node-sass sass/main.scss css/style.css -w",
		"devserver": "live-server --browser=chrome",
		"start": "npm-run-all --parallel devserver watch:sass",
		"compile:sass": "node-sass sass/main.scss css/style.comp.css",
		"prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/style.comp.css -o css/style.prefix.css",
		"compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
		"build:css": "npm-run-all compile:sass prefix:css compress:css"
		// <-- 	UUE PROJEKTI JAOKS COPY SEE KUNI SIIT
	},
	"author": "Highway Media OÜ",
	"license": "ISC",
	"devDependencies": {
			// UUE PROJEKTI JAOKS COPY SEE ALATES SIIT -->
		"node-sass": "^5.0.0",
		"autoprefixer": "^7.1.4",
		"concat": "^1.0.3",
		"npm-run-all": "^4.1.1",
		"postcss-cli": "^4.1.1"
				// <-- 	UUE PROJEKTI JAOKS COPY SEE KUNI SIIT
	}
}
```