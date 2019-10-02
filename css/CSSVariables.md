### CSS Variables

CSS Officially supports custom property (variables)

Declare:
```css
:root {
  --base: #ffc600;
  --spacing: 10px;
  --blur: 10px;
}
```

Use:
```css
img {
  padding: var(--spacing);
  filter: blur(var(--blur));
  background-color: var(--base);
}
```

Using Javascript:
```javascript
document.documentElement.style.getProperty('--spacing'); // 10px
document.documentElement.style.setProperty('--spacing', '50px');
```
