---
title: "メタデータ (DB2ToSQL) 保存 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9a76083e-4902-449e-b125-7e9259fc37f7
caps.latest.revision: "3"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 51b6e2d6e74233ce04934fbd80c410482e4bd89f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="save-metadata-db2tosql"></a>メタデータ (DB2ToSQL) の保存します。
**メタデータの保存** ダイアログ ボックスでは、SSMA プロジェクトにメタデータを保存する前にロードするように求められます。 オフラインで使用したり、テクニカル サポート担当者など、他の人に送信できる完全なプロジェクト ファイルがあるこのできます。  
  
アクセスする、**メタデータの保存**ダイアログ ボックスで、プロジェクトを保存します。 すべてのメタデータが不足している場合は、SSMA が表示されます、**メタデータの保存** ダイアログ ボックス。  
  
## <a name="options"></a>および  
**名前**  
プロジェクト内の各データベースの名前。  
  
**ステータス**  
SSMA プロジェクトにメタデータが読み込まれる場合、またはメタデータが不足している場合を示します。  
  
SSMA は、必要に応じて、プロジェクトにメタデータを読み込みます。 参照メタデータのスキーマを変換すると、メタデータが自動的に読み込まれます。  
  
**[すべて選択]**  
一覧内のすべてのデータベースを選択します。  
  
**Clear**  
メタデータの欠落しているすべてのデータベースのチェック ボックスをクリアします。 メタデータが読み込まれている場合は、チェック ボックスをオフすることはできません。  
  
**および**  
メタデータが欠落している選択したデータベースのメタデータを読み込み、プロジェクトを保存します。  
  
**キャンセル**  
保存を取り消す操作します。 メタデータの欠落がプロジェクトに読み込まれていません。  
  
