#### Basic command list

Create folder in and file in

```bash
 app\Helpers\helpers.php
```

Now in composer json e update autodload

```bash
 "autoload-dev": {
        "psr-4": {
            "Tests\\": "tests/"
        },
        "files": [
            "app/Helpers/helpers.php"
        ]
    },
```

Tar por composer update dite hobe 

```bash
 composer dump-autoload
```

Tar por helper gulo use kora jabe 

```bash
//initial
if(!function_exists('developer')){
    function developer(){
        return "Baizid MD Ashadzzaman";
    }
}

//and call
 developer()
```