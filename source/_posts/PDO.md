---
title: PDO
date: 2019-03-28 15:26:58
tags:
---
[TOC]

#### 数据库连接
```php
//setting.php
$setting = [
    'host' => '127.0.0.1',
    'port' => '3306',
    'name' => 'acme',
    'username' => 'USERNAME',
    'password' => 'PASSWORD',
    'charset' => 'utf8'
];
```
```php
include('../setting.php');
try {
    $DSN = sprintf('mysql:host=%s;dbname=%s;port=%s;charset=%s',
    $setting['host'],
    $setting['name'],
    $setting['port'],
    $setting['charset']);
    $pdo = new PDO($DSN,$setting['username'],$setting['password']);
} catch(PDOException $e){
    //连接数据库失败
    echo "Database connection failed";
    exit;
}
```

#### 预处理语句
```php
$sql = 'SELECT email FROM users WHERE id = :id';
//通过pdo实例的prepare()方法获得预处理语句对象
$statement = $pdo->prepare($sql);
$userId = filter_input(INPUT_GET, 'id');
$statement->bindValue(':id', $userId, PDO::PARAM_INT);

//指定数据类型的PDO常量:
PDO::PARAM_BOOL
PDO::PARAM_NULL
PDO::PARAM_INT
PDO::PARAM_STR  (默认值)
```

#### 查询结果
```php
//调用预处理语句的execute()方法后会使用绑定的所有数据执行SQL语句.
对于INSERT,UPDATE,DELETE语句,调用execute()后工作就结束了.
如果是SELECT语句,我们还需调用预处理语句的fetch(),fetchAll(),fetchColumn(),fetchObject()方法,获取查询结果.
```

#### 事务
```php
//把想执行的SQL语句放在PDO实例的beginTransaction()方法和commit()方法之间.
//查询语句
$stmtSubtract = $pdo->prepare('UPDATE     accounts SET amount = amount - :amount WHERE name = :name');
$stmtAdd = $pdo->prepare('UPDATE accounts SET amount = amount + :amount WHERE name = :name');
//开始事务
$pdo->beginTransaction();

//从账户1中取钱
$fromAccount = 'Checking';
$withdrawal = 50;
$stmtSubtract->bindParam(':name', $fromAccount);
$stmtSubtract->bindParam(':amount', $withdrawal, PDO::PARAM_INT);
$stmtSubtract->execute();

//把钱存入账户2
$toAccount = 'Savings';
$deposit = 50;
$stmtAdd->bindParam(':name', $toAccount);
$stmtAdd->bindParam(':amount', $withdrawal, PDO::PARAM_INT);
$stmtAdd->execute();

//提交事务
$pdo->commit();
```

![](images/6930.jpg_wh1200.jpg)
![](images/256725-1P12222341921.jpg) 
fhauifehf
```

