### How to vertical align center properly?
Using transform is the best.
```css
.center {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```
