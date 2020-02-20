---
title: '手順 1: PHP 開発用に開発環境を構成する | Microsoft Docs'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0bce6022-00bd-45c6-9671-eaa9dfa395a8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc923e3f6e24290f7f2c869fa15dfa4305776452
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "68014875"
---
# <a name="step-1-configure-environment-for-php-development"></a>手順 1: PHP 開発用に環境を構成する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]




* 次に示すように、使用する PHP ドライバーのバージョンを、ご利用の環境に基づいて特定します。[Microsoft SQL Server 用 Drivers for PHP のシステム要件](../../connect/php/system-requirements-for-the-php-sql-driver.md)
* ここから該当する PHP ドライバーをダウンロードしてインストールします。[Microsoft PHP Driver のダウンロード](https://www.microsoft.com/download/details.aspx?id=20098)  
* ここから該当する ODBC ドライバーをダウンロードしてインストールします。[ODBC Driver for SQL Server のダウンロード](../../connect/odbc/download-odbc-driver-for-sql-server.md)  
* ご利用の特定のオペレーティング システムに合わせて PHP ドライバーと Web サーバーを構成します。

### <a name="windows"></a>Windows  
  

* 次に示すように、PHP ドライバーの読み込みを構成します。[Microsoft SQL Server 用 Drivers for PHP を読み込む](../../connect/php/loading-the-php-sql-driver.md) 
* 次に示すように、PHP アプリケーションをホストするように IIS を構成します。[SQL Server 用 Microsoft Drivers for PHP に対する IIS の構成](../../connect/php/configuring-iis-for-php-sql-driver.md)

### <a name="linux-and-mac"></a>Linux と Mac


*   次に示すように、PHP ドライバーの読み込みを構成し、PHP アプリケーションをホストするようにご利用の Web サーバーを構成します。[PHP Linux と Mac ドライバーのインストールのチュートリアル](../../connect/php/installation-tutorial-linux-mac.md)
