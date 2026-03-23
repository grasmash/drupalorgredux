# Ticker Logo Image URLs

## Companies with existing Simple Icons SVGs (no image needed)
- NASA
- Tesla
- BBC
- Pinterest
- General Electric

## Companies needing image URLs (all verified 200 OK)

```
Company: UNICEF
URL: https://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/Logo_of_UNICEF.svg/250px-Logo_of_UNICEF.svg.png
Works: yes
Notes: Blue logo on transparent background. Use CSS filter: brightness(0) invert(1) for white on dark bg.
```

```
Company: Pfizer
URL: https://upload.wikimedia.org/wikipedia/commons/thumb/5/57/Pfizer_%282021%29.svg/250px-Pfizer_%282021%29.svg.png
Works: yes
Notes: 2021 rebrand logo. Blue on transparent. Use CSS filter for white version.
```

```
Company: Harvard
URL: https://upload.wikimedia.org/wikipedia/commons/thumb/c/cc/Harvard_University_coat_of_arms.svg/250px-Harvard_University_coat_of_arms.svg.png
Works: yes
Notes: Coat of arms / shield logo. Dark red (crimson) on transparent. Use CSS filter for white version.
```

```
Company: The Economist
URL: https://upload.wikimedia.org/wikipedia/commons/thumb/6/65/The_Economist_Logo.svg/250px-The_Economist_Logo.svg.png
Works: yes
Notes: Red text logo on transparent. Use CSS filter for white version.
```

```
Company: Johnson & Johnson
URL: https://upload.wikimedia.org/wikipedia/commons/thumb/b/be/JNJ_Logo_New.svg/250px-JNJ_Logo_New.svg.png
Works: yes
Notes: New J&J rebrand logo (2023). Red on transparent. Alt classic script logo also available at: https://upload.wikimedia.org/wikipedia/commons/thumb/c/cd/Johnson_and_Johnson_Logo.svg/250px-Johnson_and_Johnson_Logo.svg.png
```

```
Company: Charles Schwab
URL: https://upload.wikimedia.org/wikipedia/commons/thumb/4/4b/Charles_Schwab_Corporation_logo.svg/250px-Charles_Schwab_Corporation_logo.svg.png
Works: yes
Notes: Blue logo on transparent. Use CSS filter for white version.
```

```
Company: Amnesty International
URL: https://upload.wikimedia.org/wikipedia/en/thumb/e/ee/Amnesty_International_logo.svg/250px-Amnesty_International_logo.svg.png
Works: yes
Notes: Yellow candle/barbed wire logo. Note: hosted on en.wikipedia (non-free), not commons. May have hotlinking restrictions in some contexts.
```

```
Company: The Weather Channel
URL: https://upload.wikimedia.org/wikipedia/commons/thumb/7/77/The_Weather_Channel_logo_2005-present.svg/250px-The_Weather_Channel_logo_2005-present.svg.png
Works: yes
Notes: 2005-present logo. Use CSS filter for white version on dark bg.
```

```
Company: University of Oxford
URL: https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Oxford-University-Circlet.svg/250px-Oxford-University-Circlet.svg.png
Works: yes
Notes: Oxford circlet crest. Dark blue on transparent. Use CSS filter for white version.
```

## CSS tip for dark backgrounds

To make any colored logo appear white on a dark ticker background:
```css
.ticker-logo img {
  filter: brightness(0) invert(1);
  height: 40px;
  width: auto;
}
```

## Scaling

All URLs use 250px width. To get larger versions, change the `250px` in the URL to `500px`, `800px`, etc. (up to `1280px` for most). Example:
- 250px: `.../250px-Logo_of_UNICEF.svg.png`
- 500px: `.../500px-Logo_of_UNICEF.svg.png`
