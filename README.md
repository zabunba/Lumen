# LumenCSS-LCSS
LumenCSS is a preprocessor that create dynamic styles similar so SCSS but a bit more different

## LumenCSS
**Lumen** offers a programming style approach, like SCSS and SASS.

**Lumen** will try to have the best syntax, making so popular language syntax incorporated on the code by making possible to combine :
> C
> JavaScript
> Python



### **Lumen code**

> Lumen Test Code :

```.l
@file "_variables.lumen";

@var text-color = #333;
@rest spacing = [5px, 10px, 15px, 20px];

@func rounded-border($width, $color) {
    border: $width solid $color;
    border-radius: ($width * 2.5);
}

@block base-typography {
    font-family: sans-serif;
    font-size: 16px;
    line-height: 1.5;
}

@class card {
    @join @block centered-flex;
    padding: spacing[3];
    background: #f8f9fa;
}

@element button {
    @extend @class card;
    @get rounded-border(2px, primary-color);
    color: #fff;
    background-color: primary-color;
    cursor: pointer;
    padding: spacing[2] spacing[4];

    @child @element span {
        font-weight: bold;
        @all @class icon {
            margin-left: spacing[2];
            transform: translateY(2px);
        }
    }

    @first @element small {
        display: block;
        font-size: 12px;
    }
}

@id header {
    height: 60px;
    @and @element footer {
        background-color: #efefef;
        padding: spacing[3];
    }
}

@for $i from 1 to 11 step 5 {
    @class p-$i {
        padding: ($i * 10)px;
    }
}

@rule keyframes fade-in {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@class modal {
    @join @block base-typography;
    animation: fade-in 0.3s ease-out;
}

@rest theme = "greg";


@if theme == "dark" {
    @class dark-theme {
        background-color: #222;
        color: #eee;
    }
} @elseif theme == "light" {
    @class F-theme {
        background-color: #f8f8f8;
        color: #333;
    }
} @elseif theme == "greg" {
    @class g-theme {
        background-color: #f8f8f8;
        color: #333;
    }
} @else {
    @class f-theme {
        background-color: #6c757d;
        color: white;
    }
}

@rest i = 1;

@while i <= 7 {
    @class cr-$i {
        padding-left: (i * 10)px;
    }
    @set i = i + 1;
}


```

> Expected Output :

```.css
:root {
    --primary-color: #007bff;
    --text-color: #333;
}

.card {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15px;
    background: #f8f9fa;
}
.cr-1 {
    padding-left: 10px;
}
.cr-2 {
    padding-left: 20px;
}
.cr-3 {
    padding-left: 30px;
}
.cr-4 {
    padding-left: 40px;
}
.cr-5 {
    padding-left: 50px;
}
.cr-6 {
    padding-left: 60px;
}
.cr-7 {
    padding-left: 70px;
}
.f-theme {
    background-color: #6c757d;
    color: white;
}
.math-1 {
    color: red; background: red;
}
.modal {
    font-family: sans-serif;
    font-size: 16px;
    line-height: 1.5;
    animation: fade-in 0.3s ease-out;
}
.p-1 {
    padding: 10px;
}
.p-11 {
    padding: 110px;
}
.p-6 {
    padding: 60px;
}
button {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px 20px;
    background: #f8f9fa;
    color: #fff;
    background-color: var(--primary-color);
    cursor: pointer;
}
button > span {
    font-weight: bold;
}
button > span .icon {
    margin-left: 10px;
    transform: translateY(2px);
}
button + small {
    display: block;
    font-size: 12px;
}
#header {
    height: 60px;
}
#header, footer {
    background-color: #efefef;
    padding: 15px;
}
@keyframes fade-in {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
```
