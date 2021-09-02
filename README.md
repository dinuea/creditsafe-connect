# Creditsafe API

![Tests](https://github.com/SynergiTech/creditsafe-connect/workflows/Tests/badge.svg)

```
composer require dinuea/creditsafe-connect
```

## Usage

### Setting up Client
```php
$config = [
    'username'  =>  'username',
    'password'  =>  'password'
];

$creditsafe = new \SynergiTech\Creditsafe\Client($config);
```

### Access countries and their codes
```php
$creditsafe->countries()->access();
```

### Search criteria using country code
```php

$creditsafe->companies()->searchCriteria(['countries' => 'GB']);


```
### Company search pagination
```php
$search = $creditsafe->companies()->search(['countries' => 'GB', 'name' => 'GOOGLE UK LIMITED']);
$search->setPageSize(100);
foreach ($search as $result) {
    $company = $result->get();
}
```

### Get company report
```php
$company=$creditsafe->companies()->get('GB001-0-03977902');

$directors=$company->getCurrentDirectors();
$shareholders=$company->getShareHolders();
$personsWithSignificantControl=$company->getPersonsWithSignificantControl();
```

## Running tests
```
vendor/bin/phpunit tests
```
