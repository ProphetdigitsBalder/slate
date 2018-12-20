# Category

## Category List Without Login

### Description

| Title | Description |
| -------: | :---- |
| URL | `company/{company_id}/category/list` |
| Method | `get` |
| Use | to get company category |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| company_id | integer | company id which user want get category list |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name": "Root",
    "subCategories": [{
        "id": 2,
        "name": "Category Test",
        "subCategories": []
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | category id |
| name | string | category name |
| subCategories | object | property same as above |

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**company not exist:** current company not exist|


## Category List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/category/list` |
| Method | `post` |
| Use | to get company category |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "target_company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| target_company_id | integer | The company id of category |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name": "Root",
    "subCategory": [{
        "id": 2,
        "name": "Category Test",
        "subCategory": [],
        "items": []
    }],
    "items": [{
        "id": 1,
        "number": "item number",
        "name": "item name",
        "cover_img": {
            "240p": "asdsad_240p.jpeg",
            "480p": "asdsad_480p.jpeg",
            "720p": "asdsad_720p.jpeg",
            "1080p": "asdsad_1080p.jpeg"
        }
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The category id |
| name | string | The category name |
| items | array | The items belong to current category |
| subCategory | array | The subCategories of current category <br />The content same as category |

| category_item | | |
| -------: | :---- | :--- |
| id | integer | The id of item |
| number | string | The number of item |
| name | string | The name of item |
| cover_img | object | The cover image of item <br />It will be empty if no set cover image |

| category_item_cover_img | | |
| -------: | :---- | :--- |
| 240p | string | The url of picture for 240 resolution  (426x240) |
| 480p | string | The url of picture for 480 resolution (854x480) |
| 720p | string | The url of picture for 720 resolution (1280x720) |
| 1080p | string | The url of picture for 1080 resolution (1920x1080) |

> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>does not signin: The api_key is invalid</li><li>not select company yet: The user has not select current company</li><li>company not exist: current company not exist</li><li>not company member: the user is not the company member</li></ul> |


## Category Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/category/detail` |
| Method | `post` |
| Use | to show category detail, items belongs to current category and all items belongs to sub-category |
| Notice | |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "target_company_id": 1,
    "category_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| target_company_id | integer | The company id of category |
| category_id | integer | The id of category |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name": "Category Name",
    "description": "",
    "parent": {
        "id": "",
        "name": "",
        "specs": [],
        "customizations": []
    },
    "specs": [{
        "id": 1,
        "name": "Spec Name"
    }],
    "spec2s": [{
        "id": 1,
        "name": "Spec Name",
        "part": true
    }],
    "customizations": [{
        "id": 1,
        "name": "Customization  Name"
    }],
    "subCategory":[{
        "id":"1",
        "name":"Mountain Bike"
    },{
        "id":"2",
        "name":"Road Bike"
    }],
    "all_items": [],
    "items":[{
        "id": 1,
        "number": "item-1",
        "name": "Edison Evo",
        "company_id": 1,
        "cover_img": {
            "240p": "http://abc/xxx_240p.jpg",
            "480p": "http://abc/xxx_480p.jpg",
            "720p": "http://abc/xxx_720p.jpg",
            "1080p": "http://abc/xxx_1080p.jpg"
        }
    },{
        "id": 2,
        "number": "item-2",
        "name": "Cargo",
        "company_id": 1,
        "cover_img": {}
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of category |
| name | string | The name of category |
| description | string | The description of category |
| parent | object | The parent of category |
| specs | array | The specs connect with category |
| spec2s | array | The new specs connect with category |
| customizations | array | The customizations connect with category |

| category_parent | | |
| -------: | :---- | :--- |
| id | integer | The id of parent category |
| name | string | The name of parent category |
| specs | array | The parent own specs include parent’s parent… <br />content same to category_spec |
| spec2s | array | The parent own new specs include parent’s parent… <br />content same to category_spec |
| customizations | array | The parent own customizations include parent’s parent… <br />content same to category_customization |
| subCategory | array | The sub categories of current category |
| items | array | The items belongs to current category |
| all_items | array | The items belongs to current category and subcategory and subsubcategory… <br />content same to category_item |

| category_spec | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| display_name | string | The display name of spec |
| values | array | The values of spec |

| category_spec_value | | |
| -------: | :---- | :--- |
| id | integer | The id of value |
| name | string | The name of value |

 category_spec2 | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |
| part | boolean | The part of spec |

| category_customization | | |
| -------: | :---- | :--- |
| id | integer | The id of customization |
| name | string | The name of customization |
| display_name | string | The display name of customization |

| category_subCategory | | |
| -------: | :---- | :--- |
| id | integer | The id of category |
| name | string | The name of category |

| category_item | | |
| -------: | :---- | :--- |
| id | integer | The id of item |
| name | string | The name of item |
| number | string | The number of item |
| price | number | The price of item |
| currency | string | The default currency of company |
| company_id | integer | The id of company of item |
| cover_img | object | The cover image of item. It will be empty if no set cover image |

| category_item_cover_img | | |
| -------: | :---- | :--- |
| 240p | string | The url of picture for 240 resolution  (426x240) |
| 480p | string | The url of picture for 480 resolution (854x480) |
| 720p | string | The url of picture for 720 resolution (1280x720) |
| 1080p | string | The url of picture for 1080 resolution (1920x1080) |

> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** current company not exist|
|||**not company member:** the user is not the company member|
|||**category not exist:** category id is incorrect|
|||**illegal form input':** form format does not pass validation|


## Create Category

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/category/create` |
| Method | `post` |
| Use | to create category |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "name": "category name",
    "description": "",
    "parent_id": 1,
    "specs": [1, 2, 3],
    "spec2s": [1, 2, 3],
    "customizations": [1, 2, 3]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| name | string | The name of category |
| description | string | The comment of category |
| parent_id | integer | The parent id of current category |
| specs | array | The id set of spec |
| spec2s | array | The id set of new spec |
| customizations | array | The id set of customization |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "category" : {
        "id": 1,
        "name": "Category Name",
        "description": "",
        "parent": {
            "id": "",
            "name": ""
        },
        "specs": [{
            "id": 1,
            "name": "Spec Name"
        }]
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of category |
| name | string | The name of category |
| description | string | The comment of category |
| parent | object | The parent of category |
| specs | array | The specs connect with category |

| category_parent | | |
| -------: | :---- | :--- |
| id | integer | The id of parent category |
| name | string | The name of parent category |

| category_spec | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |


> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "validation": {
        "name": ["dulicate"],
        "parent_id": ["required"]
    },
    "error_name": "illegal form input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| **validation** | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |
| name | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| description | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| parent_id | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol>
| specs | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id of spec is not exist</li><li>The spec is not belongs to the current company </li></ol>
| customizations | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id of customization is not exist</li><li>The customization is not belongs to the current company </li></ol>
| spec2s | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id of spec is not exist</li><li>The spec is not belongs to the current company </li></ol>



## Category Detail Without Login

### Description

| Title | Description |
| -------: | :---- |
| URL | `category/{category_id}/detail` |
| Method | `get` |
| Use | to show category detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "page": 1,
    "perpage": 2
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| page | integer(option) | the page of all items list, page < 0 will set to first page, page > last page will set to last page, default: 1 |
| perpage | integer(option) | items per page, default: 60 |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 1,
    "name": "Category Name",
    "items":[{
        "id": 1,
        "name": "Edison Evo",
        "cover_img": {
            "px240": "http://abc/xxx_240p.jpg",
            "px480": "http://abc/xxx_480p.jpg",
            "px720": "http://abc/xxx_720p.jpg",
            "px1080": "http://abc/xxx_1080p.jpg"
        },
        "images": [{
            "name": "xxx.jpg",
            "cover": 0,
            "resource": {
                "px240": "http://abc/xxx_240p.jpg",
                "px480": "http://abc/xxx_480p.jpg",
                "px720": "http://abc/xxx_720p.jpg",
                "px1080": "http://abc/xxx_1080p.jpg"
            }
        },{
            "name": "yyy.jpg",
            "cover": 1,
            "resource": {
                "px240": "http://abc/yyy_240p.jpg",
                "px480": "http://abc/yyy_480p.jpg",
                "px720": "http://abc/yyy_720p.jpg",
                "px1080": "http://abc/yyy_1080p.jpg"
            }
        }],
        "currency": "EUR",
        "price": 10
    }],
    "pager": {
        "total": 31,
        "per_page": 2,
        "current_page": 1,
        "last_page": 16
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | category id |
| name | string | category name |
| **items** | **array** | items in this category |
| *id* | integer | item id |
| *name* | string | item name |
| *price* | number | item price |
| *currency* | string | default currency name of company |
| *cover_img* | **object** | item cover image. It will be empty if no set cover image |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |
| **images** | **object** | It will get item images .It will be empty if there is no item image |
| *name* | string | file name which get from back end after specific image has been updated |
| *cover* | boolean | cover image tag |
| *resource* | **object** | cover image tag |
| *px240* | string | picture url of 240 resolution (426x240) |
| *px480* | string | picture url of 480 resolution (854x480) |
| *px720* | string | picture url of 720 resolution (1280x720) |
| *px1080* | string | picture url of 1080 resolution (1920x1080) |
| **pager** | **object** | items pager |
| *total* | integer | total number of data records |
| *per_page* | integer | items per page for input |
| *current_page* | integer | current page number |
| *last_page* | integer | last page number |

> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**company not exist:** current company not exist|
|||**category not exist:** category id is incorrect|
|||**illegal form input':** form format does not pass validation|


## Edit Category

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/category/edit` |
| Method | `post` |
| Use | to edit category |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "id": 1,
    "name": "category name",
    "description": "",
    "parent_id": 1,
    "specs": [1, 2, 3],
    "spec2s": [1, 2, 3],
    "customizations": [1, 2, 3]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | System gives it after user sign in |
| id | integer | The id of category |
| name | string (option) | The name of category |
| description | string (option) | The description of category |
| parent_id | integer (option) | The parent id of category |
| specs | array (option) | The id set of spec |
| spec2s | array (option) | The id set of new spec |
| customizations | array (option) | The id set of customization |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "category" : {
        "id": 1,
        "name": "Category Name",
        "description": "",
        "parent": {
            "id": "",
            "name": ""
        },
        "specs": [{
            "id": 1,
            "name": "Spec Name"
        }],
    }
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The id of category |
| name | string | The name of category |
| description | string | The comment of category |
| parent | object | The parent of category |
| specs | array | The specs connect with category |

| category_parent | | |
| -------: | :---- | :--- |
| id | integer | The id of parent category |
| name | string | The name of parent category |

| category_spec | | |
| -------: | :---- | :--- |
| id | integer | The id of spec |
| name | string | The name of spec |


> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "validation": {
        "name": ["dulicate"],
        "parent_id": ["required"]
    },
    "error_name": "illegal form input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The name of wrong type <br/><ul><li>not_sign_in: The api_key is invalid</li><li>not_select_company: The user has not select current company</li><li>illegal_form_input: The form format does not pass validation</li></ul> |
| **validation** | object (option) | if the err_name is 'illegal_form_input', system should assign the name of wrong type for each error input |
| id | array (option) | required: <ol><li>The field is required</li></ol><br />invalid: <ol><li>The data is not integer</li><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol>
| name | array (option) | required: <ol><li>The field is required</li><li>The data is empty</li></ol><br />invalid: <ol><li>The data is not string</li></ol> |
| description | array (option) | invalid: <ol><li>The data is not string</li></ol> |
| parent_id | array (option) | invalid: <ol><li>The data is not integer</li><li>The id of category is not exist</li><li>The category is not belongs to the current company </li></ol>
| specs | array (option) | invalid: <ol><li>The data is not integer</li><li>The id of spec is not exist</li><li>The spec is not belongs to the current company </li></ol>
| customizations | array (option) | invalid: <ol><li>The data is not integer</li><li>The id of customization is not exist</li><li>The customization is not belongs to the current company </li></ol>
| spec2s | array (option) | invalid: <ol><li>The data is not integer</li><li>The id of spec is not exist</li><li>The spec is not belongs to the current company </li></ol>




## Delete Category

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/category/delete` |
| Method | `post` |
| Use | to delete category |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "category_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| category_id | integer | category id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| (Nothing return) | - | - |

> Return Parameters When Failure

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** current company not exist|
|||**not company member:** the user is not the company member|
|||**category not exist:** category id is incorrect|
