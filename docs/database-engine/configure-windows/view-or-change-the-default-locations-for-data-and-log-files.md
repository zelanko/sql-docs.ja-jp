---
title: データ ファイルとログ ファイルの既定の場所の表示または変更 | Microsoft Docs
description: SQL Server のデータ ファイルとログ ファイルの既定の場所を表示または変更する方法について説明します。 アクセス制御リスト (ACL) を使用してファイルを保護する方法について説明します。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9a0c720684f0eefa301e9a5387ffda54e349f85d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85680784"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>データ ファイルとログ ファイルの既定の場所の表示または変更
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
 データ ファイルとログ ファイルを保護するために、それらがアクセス制御リスト (ACL) によって保護されていることを確認します。 ACL は、ファイルを作成するディレクトリのルートに設定します。  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>データベース ファイルの既定の場所を表示または変更する  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックして **[プロパティ]** をクリックします。  
  
2.  その [プロパティ] ページの左側のパネルで、 **[データベースの設定]** タブをクリックします。  
  
3.  **[データベースの既定の場所]** パネルに、新しいデータ ファイルと新しいログ ファイルの現在の既定の場所が表示されます。 既定の場所を変更するには、 **[データ]** フィールドまたは **[ログ]** フィールドに新しい既定のパス名を入力するか、参照ボタンをクリックしてパス名を選択します。  
  
>**注:** 既定の場所を変更したら、SQL Server サービスを停止して開始することで変更を完了する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [データベースの作成](../../relational-databases/databases/create-a-database.md)  
  
  
