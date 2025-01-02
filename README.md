```css
.slides-container {
    width: 1000px;
    height: 500px;
    position: relative;
    overflow: hidden;
}

.slide {
    position: absolute;
    width: 100%;
    height: 100%;
    animation: slideShow 4s infinite;
    opacity: 0;
}

/* Stagger the animation delay for each slide */
.slide:nth-child(1) { animation-delay: 0s; }
.slide:nth-child(2) { animation-delay: 1s; }
.slide:nth-child(3) { animation-delay: 2s; }
.slide:nth-child(4) { animation-delay: 3s; }

@keyframes slideShow {
    0%, 25% {
        opacity: 1;
        transform: translateX(0);
    }
    30%, 100% {
        opacity: 0;
        transform: translateX(-100%);
    }
}

/* Center the container */
main {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
}

/* Reset default margins */
body {
    margin: 0;
    padding: 0;
}
```

### Every second
```css
body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
}

main {
    width: 100%;
    height: 100vh;
}

.slides-container {
    width: 100%;
    height: 100vh;
    position: relative;
    overflow: hidden;
}

.slide {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    animation: slideShow 4s infinite;
    opacity: 0;
    transition: opacity 0.5s ease-in-out;
}

/* Stagger the animation delay for each slide */
.slide:nth-child(1) { animation-delay: 0s; }
.slide:nth-child(2) { animation-delay: 1s; }
.slide:nth-child(3) { animation-delay: 2s; }
.slide:nth-child(4) { animation-delay: 3s; }

@keyframes slideShow {
    0%, 23% {
        opacity: 1;
        transform: translateX(0);
    }
    25%, 100% {
        opacity: 0;
        transform: translateX(-100%);
    }
}
```

### Looking very odd in disappearing

```css
body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
}

main {
    width: 100%;
    height: 100vh;
}

.slides-container {
    width: 100%;
    height: 100vh;
    position: relative;
    overflow: hidden;
}

.slide {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    animation: slideShow 16s infinite;  /* Increased total animation duration */
    opacity: 0;
    transition: all 1.5s ease-in-out;  /* Smoother transition */
}

/* Stagger the animation delay for each slide */
.slide:nth-child(1) { animation-delay: 0s; }
.slide:nth-child(2) { animation-delay: 4s; }  /* Each slide shows for 4 seconds */
.slide:nth-child(3) { animation-delay: 8s; }
.slide:nth-child(4) { animation-delay: 12s; }

@keyframes slideShow {
    0%, 20% {
        opacity: 1;
        transform: scale(1.05);  /* Slight zoom effect */
    }
    25%, 100% {
        opacity: 0;
        transform: scale(1) translateX(-100px);
    }
}
```
### Right to left working fine (white in middle)

```css
body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
}

main {
    width: 100%;
    height: 100vh;
}

.slides-container {
    width: 100%;
    height: 100vh;
    position: relative;
    overflow: hidden;
}

.slide {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    animation: slideShow 16s infinite;
    opacity: 0;
    transition: all 1.5s ease-in-out;
    transform: translateX(100%);  /* Start position from right */
}

/* Stagger the animation delay for each slide */
.slide:nth-child(1) { animation-delay: 0s; }
.slide:nth-child(2) { animation-delay: 4s; }
.slide:nth-child(3) { animation-delay: 8s; }
.slide:nth-child(4) { animation-delay: 12s; }

@keyframes slideShow {
    0% {
        opacity: 0;
        transform: translateX(100%);  /* Start from right */
    }
    5%, 20% {
        opacity: 1;
        transform: translateX(0);  /* Move to center */
    }
    25%, 100% {
        opacity: 0;
        transform: translateX(-100%);  /* Exit to left */
    }
}
```
### sliding image one after one (not infinite loop)
```css
body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
}

main {
    width: 100%;
    height: 100vh;
}

.slides-container {
    width: 100%;
    height: 100vh;
    position: relative;
    overflow: hidden;
}

.slide {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    animation: slideShow 16s infinite;
    opacity: 1; /* Changed from 0 to 1 */
    transform: translateX(100%);
}

.slide:nth-child(1) { animation-delay: 0s; }
.slide:nth-child(2) { animation-delay: 4s; }
.slide:nth-child(3) { animation-delay: 8s; }
.slide:nth-child(4) { animation-delay: 12s; }

@keyframes slideShow {
    0%, 5% {
        transform: translateX(100%);
    }
    20%, 45% {
        transform: translateX(0);
    }
    60%, 100% {
        transform: translateX(-100%);
    }
}
```

## The perfect sliding loop

```css
body, html {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
}

main {
    width: 100%;
    height: 100vh;
}

.slides-container {
    width: 100%;
    height: 100vh;
    position: relative;
    overflow: hidden;
}

.slide {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    animation: slideShow 16s infinite;
    opacity: 1;
    transform: translateX(100%);
}

.slide:nth-child(1) { animation-delay: 0s; }
.slide:nth-child(2) { animation-delay: 4s; }
.slide:nth-child(3) { animation-delay: 8s; }
.slide:nth-child(4) { animation-delay: 12s; }

@keyframes slideShow {
    0% {
        transform: translateX(100%);
    }
    5%, 25% {
        transform: translateX(0);
    }
    30%, 100% {
        transform: translateX(-100%);
    }
}
```


