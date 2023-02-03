# kira

A simple templating language/tool to generate files from templates and data stored in json format.

## Usage

### Running the tool

```powershell
python kira.py --template my_folder --data my_data.json --output my_result
```

**--template:** The folder that contains all the templates files.

--data: The JSON file that contains the data to generate the templates.

--output: The output folder where the resulting folders/files will be stored after generation.

### The data

The data to generate the files from the templates should be in JSON format inside the data dictionary. This document should also contain the tokens to use in the templates to reference the data.

Example:

```json
{
    "fruits-fruit": [
        {
            "name": "apple",
            "color": "red"
        },
        {
            "name": "banana",
            "color": "yellow"
        },
        {
            "name": "orange",
            "color": "orange"
        }
    ]
}
```

### The templates

All the files inside the folder will be generated following the rules:

Files and folders:

```
- my_folder
  |- @fruit#.jsonc
```

The result:

```
- my_result
  |- apple.json
  |- banana.json
  |- orange.json

```

File *@fruit#.jsonc* content:

```json
{
    "id": "@fruit#",
    "identifier": "@fruit.name#",
    "color": "@fruit.color#"
}
```

The generated banana.json file:

```json
{
    "id": "1",
    "identifier": "banana",
    "color": "yellow"
}
```
