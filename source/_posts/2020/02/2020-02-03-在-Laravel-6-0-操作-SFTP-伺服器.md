---
title: 在 Laravel 6.0 操作 SFTP 伺服器
permalink: 在-Laravel-6-0-操作-SFTP-伺服器
date: 2020-02-03 14:50:00
tags: ["程式設計", "PHP", "Laravel", "SFTP"]
categories: ["程式設計", "PHP", "Laravel"]
---

## 做法

安裝套件。

```BASH
composer require league/flysystem-sftp
```

修改 `config/filesystems.php` 檔，新增一個儲存系統：

```PHP
return [

    // ...

    'disks' => [

        // ...

        'sftp' => [
            'driver' => 'sftp',
            'host' => env('SFTP_HOST'),
            'port' => env('SFTP_PORT'),
            'username' => env('SFTP_USERNAME'),
            'password' => env('SFTP_PASSWORD'),
        ],

    ],

];
```

修改 `.env` 檔：

```ENV
SFTP_HOST=
SFTP_PORT=
SFTP_USERNAME=
SFTP_PASSWORD=
```

取得檔案：

```PHP
\Illuminate\Support\Facades\Storage::disk('sftp')->get('file.csv');
```

參考資料

- [Laravel File Storage](https://laravel.com/docs/master/filesystem)
