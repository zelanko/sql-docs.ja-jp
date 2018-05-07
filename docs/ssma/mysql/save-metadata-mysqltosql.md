---
title: メタデータ (MySQLToSQL) 保存 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9bc6273f-e8b1-430b-81a5-14330a783562
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6f38df2f57bbc8c5e96b77f6883a16c7325cb445
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="save-metadata--mysqltosql"></a>メタデータ (MySQLToSQL) の保存します。
**メタデータの保存** ダイアログ ボックスでは、SSMA プロジェクトにメタデータを保存する前にロードするように求められます。 オフラインで使用したり、テクニカル サポート担当者など、他の人に送信できる完全なプロジェクト ファイルがあるこのできます。  
  
アクセスする、**メタデータの保存**ダイアログ ボックスで、プロジェクトを保存します。 すべてのメタデータが不足している場合は、SSMA が表示されます、**メタデータの保存** ダイアログ ボックス。  
  
## <a name="options"></a>オプション  
**名前**  
プロジェクト内の各データベースの名前。  
  
**[状態]**  
SSMA プロジェクトにメタデータが読み込まれる場合、またはメタデータが不足している場合を示します。  
  
SSMA は、必要に応じて、プロジェクトにメタデータを読み込みます。 参照メタデータのスキーマを変換すると、メタデータが自動的に読み込まれます。  
  
**[すべて選択] します。**  
一覧内のすべてのデータベースを選択します。  
  
**Clear**  
メタデータの欠落しているすべてのデータベースのチェック ボックスをクリアします。 メタデータが読み込まれている場合は、チェック ボックスをオフすることはできません。  
  
**[保存]**  
メタデータが欠落している選択したデータベースのメタデータを読み込み、プロジェクトを保存します。  
  
**キャンセル**  
保存を取り消す操作します。 メタデータの欠落がプロジェクトに読み込まれていません。  
  
