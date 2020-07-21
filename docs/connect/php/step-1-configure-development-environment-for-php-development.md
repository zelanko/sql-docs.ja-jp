---
title: 手順 1:PHP 用に環境を構成する
description: このファースト ステップ ガイドの手順 1 では、PHP と Microsoft ODBC Driver for SQL Server をインストールし、開発環境を構成します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0bce6022-00bd-45c6-9671-eaa9dfa395a8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88eb2c2c67eac3ecd9fba2c79c143de28cf60d22
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633173"
---
# <a name="step-1-configure-environment-for-php-development"></a>手順 1: PHP 開発用に環境を構成する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]




* 次に示すように、使用する PHP ドライバーのバージョンを、ご利用の環境に基づいて特定します。[Microsoft SQL Server 用 Drivers for PHP のシステム要件](system-requirements-for-the-php-sql-driver.md)
* ここから該当する PHP ドライバーをダウンロードしてインストールします。[Microsoft PHP Driver のダウンロード](https://www.microsoft.com/download/details.aspx?id=20098)  
* ここから該当する ODBC ドライバーをダウンロードしてインストールします。[ODBC Driver for SQL Server のダウンロード](../odbc/download-odbc-driver-for-sql-server.md)  
* ご利用の特定のオペレーティング システムに合わせて PHP ドライバーと Web サーバーを構成します。

### <a name="windows"></a>Windows  
  

* 次に示すように、PHP ドライバーの読み込みを構成します。[Microsoft SQL Server 用 Drivers for PHP を読み込む](../../connect/php/loading-the-php-sql-driver.md) 
* 次に示すように、PHP アプリケーションをホストするように IIS を構成します。[SQL Server 用 Microsoft Drivers for PHP に対する IIS の構成](../../connect/php/configuring-iis-for-php-sql-driver.md)

### <a name="linux-and-macos"></a>Linux と macOS


*   次に示すように、PHP ドライバーの読み込みを構成し、PHP アプリケーションをホストするようにご利用の Web サーバーを構成します。[Linux および macOS の PHP ドライバーのインストール チュートリアル](../../connect/php/installation-tutorial-linux-mac.md)
