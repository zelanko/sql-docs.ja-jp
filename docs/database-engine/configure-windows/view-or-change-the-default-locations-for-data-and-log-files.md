---
title: "データ ファイルとログ ファイルの既定の場所の表示または変更 | Microsoft Docs"
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: e1afb149a8b3348660e4e21c879598436eaaedfa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>データ ファイルとログ ファイルの既定の場所の表示または変更
  
 データ ファイルとログ ファイルを保護するために、それらがアクセス制御リスト (ACL) によって保護されていることを確認します。 ACL は、ファイルを作成するディレクトリのルートに設定します。  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>データベース ファイルの既定の場所を表示または変更する  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックして **[プロパティ]**をクリックします。  
  
2.  その [プロパティ] ページの左側のパネルで、 **[データベースの設定]** タブをクリックします。  
  
3.  **[データベースの既定の場所]**パネルに、新しいデータ ファイルと新しいログ ファイルの現在の既定の場所が表示されます。 既定の場所を変更するには、 **[データ]** フィールドまたは **[ログ]** フィールドに新しい既定のパス名を入力するか、参照ボタンをクリックしてパス名を選択します。  
  
>**注:** 既定の場所を変更したら、SQLServer サービスをいったん停止してから再起動して変更を完了する必要があります。  
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [データベースの作成](../../relational-databases/databases/create-a-database.md)  
  
  
