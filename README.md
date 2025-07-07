# LumenCSS-LCSS
LumenCSS is a preprocessor that create dynamic styles similar so SCSS but a bit more different

## LumenCSS
**Lumen** offers a programming style approach, like SCSS and SASS.


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

@for $i from 1 to 3 {
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
.modal {
    font-family: sans-serif;
    font-size: 16px;
    line-height: 1.5;
    animation: fade-in 0.3s ease-out;
}
.p-1 {
    padding: 10px;
}
.p-2 {
    padding: 20px;
}
.p-3 {
    padding: 30px;
}
button {
    color: #fff;
    background-color: var(--primary-color);
    cursor: pointer;
    padding: 15px;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f8f9fa;
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
