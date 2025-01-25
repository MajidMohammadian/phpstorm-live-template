# Useful tools for phpstorm live template

## 1. PHPStorm Live Template

### How to use
- Open PHPStorm
- Go to `File` -> `Settings` -> `Editor` -> `Live Templates`
- Click on `+` button to add new template
- Fill the `Abbreviation` and `Description` fields
- Fill the `Template text` field with the code snippet
- Click on `Define` button to define the context where the template can be used
- Click on `Apply` and `OK` buttons to save the template
- Use the abbreviation in the code editor and press `Tab` key to expand the template
- Enjoy!

### List of live template for PHP Laravel

##### `.`

```php
->
```

##### `dd` - Dump and die

```php
dd($VAR$);$END$
```

##### `epr` - Echo pre tag and var_dump

```php
echo '<pre dir="ltr">';
var_dump($VAR$);
echo '</pre>';
$END$
```

##### `epre` - Echo pre tag and var_dump with die

```php
echo '<pre dir="ltr">';
var_dump($VAR$);
echo '</pre>';
die();
$END$
```

##### `qlogs` - Query log start

```php
\DB::enableQueryLog();
global $q_log_startMemory;
$q_log_startMemory = memory_get_usage();
$END$
```

##### `qlog` - Query show log and memory usage

```php
global $q_log_startMemory;
dd([
    'Query Count' => count(\DB::getQueryLog()),
    'Queries' => \DB::getQueryLog(),
    'Memory Used' => sprintf(
        '%d GB, %d MB, %d KB, %d Bytes',
        floor((memory_get_usage() - $q_log_startMemory) / (1024 ** 3)),
        floor(((memory_get_usage() - $q_log_startMemory) % (1024 ** 3)) / (1024 ** 2)),
        floor(((memory_get_usage() - $q_log_startMemory) % (1024 ** 2)) / 1024),
        (memory_get_usage() - $q_log_startMemory) % 1024
    ),
    'Peak Memory' => sprintf(
        '%d GB, %d MB, %d KB, %d Bytes',
        floor(memory_get_peak_usage() / (1024 ** 3)),
        floor((memory_get_peak_usage() % (1024 ** 3)) / (1024 ** 2)),
        floor((memory_get_peak_usage() % (1024 ** 2)) / 1024),
        memory_get_peak_usage() % 1024
    ),
]);
$END$
```

##### `qlogb` - Query show log and memory usage in blade

```php
@php
    global $q_log_startMemory;
    dd([
        'Query Count' => count(\DB::getQueryLog()),
        'Queries' => \DB::getQueryLog(),
        'Memory Used' => sprintf(
            '%d GB, %d MB, %d KB, %d Bytes',
            floor((memory_get_usage() - $q_log_startMemory) / (1024 ** 3)),
            floor(((memory_get_usage() - $q_log_startMemory) % (1024 ** 3)) / (1024 ** 2)),
            floor(((memory_get_usage() - $q_log_startMemory) % (1024 ** 2)) / 1024),
            (memory_get_usage() - $q_log_startMemory) % 1024
        ),
        'Peak Memory' => sprintf(
            '%d GB, %d MB, %d KB, %d Bytes',
            floor(memory_get_peak_usage() / (1024 ** 3)),
            floor((memory_get_peak_usage() % (1024 ** 3)) / (1024 ** 2)),
            floor((memory_get_peak_usage() % (1024 ** 2)) / 1024),
            memory_get_peak_usage() % 1024
        ),
    ]);
@endphp
$END$
```

##### `mlogs` - use this code in the start of the function to log the model retrieval

```php
global $q_log_startModel;
$q_log_startModel = 0;
\Event::listen('eloquent.retrieved: *', function ($model) {
    global $q_log_startModel;
    $q_log_startModel++;
});
$END$
```

##### `mlog` - use this code in the end of the function to show the model retrieval log

```php
global $q_log_startModel;
dd($q_log_startModel);
$END$
```

##### `mlogb` - use this code in the end of the function to show the model retrieval log in blade

```php
@php
    global $q_log_startModel;
    dd($q_log_startModel);
@endphp
$END$
```

##### `qmlog` - Query and Model log

```php
global $q_log_startModel;
global $q_log_startMemory;
dd([
    'Query Count' => count(\DB::getQueryLog()),
    'Queries' => \DB::getQueryLog(),
    'Memory Used' => sprintf(
        '%d GB, %d MB, %d KB, %d Bytes',
        floor((memory_get_usage() - $q_log_startMemory) / (1024 ** 3)),
        floor(((memory_get_usage() - $q_log_startMemory) % (1024 ** 3)) / (1024 ** 2)),
        floor(((memory_get_usage() - $q_log_startMemory) % (1024 ** 2)) / 1024),
        (memory_get_usage() - $q_log_startMemory) % 1024
    ),
    'Peak Memory' => sprintf(
        '%d GB, %d MB, %d KB, %d Bytes',
        floor(memory_get_peak_usage() / (1024 ** 3)),
        floor((memory_get_peak_usage() % (1024 ** 3)) / (1024 ** 2)),
        floor((memory_get_peak_usage() % (1024 ** 2)) / 1024),
        memory_get_peak_usage() % 1024
    ),
    'Model Count' => $q_log_startModel,
]);
$END$
```

##### `qmlogb` - Query and Model log in blade

```php
@php
    global $q_log_startModel;
    global $q_log_startMemory;
    dd([
        'Query Count' => count(\DB::getQueryLog()),
        'Queries' => \DB::getQueryLog(),
        'Memory Used' => sprintf(
            '%d GB, %d MB, %d KB, %d Bytes',
            floor((memory_get_usage() - $q_log_startMemory) / (1024 ** 3)),
            floor(((memory_get_usage() - $q_log_startMemory) % (1024 ** 3)) / (1024 ** 2)),
            floor(((memory_get_usage() - $q_log_startMemory) % (1024 ** 2)) / 1024),
            (memory_get_usage() - $q_log_startMemory) % 1024
        ),
        'Peak Memory' => sprintf(
            '%d GB, %d MB, %d KB, %d Bytes',
            floor(memory_get_peak_usage() / (1024 ** 3)),
            floor((memory_get_peak_usage() % (1024 ** 3)) / (1024 ** 2)),
            floor((memory_get_peak_usage() % (1024 ** 2)) / 1024),
            memory_get_peak_usage() % 1024
        ),
        'Model Count' => $q_log_startModel,
    ]);
@endphp
$END$
```

##### `tcb` - Log the time taken by the code block in file

```php
try {
    $dataToLog = $VAR$ ?? '';
    if (file_put_contents(__DIR__ . DIRECTORY_SEPARATOR . 'log_data.txt', "[" . date('Y-m-d H:i:s') . "] -> " . var_export($dataToLog, true) . PHP_EOL, FILE_APPEND) === false) {
        throw new \Exception("Unable to write to log file.");
    }
} catch (\Exception $e) {
    echo "Error: " . $e->getMessage();
}
$END$
```

##### `tcbe` - Log the time taken by the code block in file with die

```php
try {
    $dataToLog = $VAR$ ?? '';
    if (file_put_contents(__DIR__ . DIRECTORY_SEPARATOR . 'log_data.txt', "[" . date('Y-m-d H:i:s') . "] -> " . var_export($dataToLog, true) . PHP_EOL, FILE_APPEND) === false) {
        throw new \Exception("Unable to write to log file.");
    }
} catch (\Exception $e) {
    echo "Error: " . $e->getMessage();
}
die();
$END$
```

##### `conl` - Console log in js

```php
console.log($d$)$END$
```