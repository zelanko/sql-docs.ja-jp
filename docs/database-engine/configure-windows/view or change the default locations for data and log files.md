---
title: "データ ファイルとログ ファイルの既定の場所の表示または変更 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログ ファイル [SQL Server]、既定の場所の変更"
  - "データ ファイル [SQL Server]、既定の場所の変更"
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
---
# データ ファイルとログ ファイルの既定の場所の表示または変更 (SQL Server Management Studio)
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、新しいデータ ファイルとログ ファイルの既定の場所を表示および変更する方法について説明します。 既定のパスはレジストリから取得されます。 場所を変更した後は、別の場所が指定されない限り、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで作成されるすべての新しいデータベースに関して、この場所が使用されます。  
  
 
##  <a name="Recommendations"></a> 推奨事項  
 データ ファイルとログ ファイルを保護するために、それらがアクセス制御リスト (ACL) によって保護されていることを確認します。 ACL は、ファイルを作成するディレクトリのルートに設定します。  
  
  
## データベース ファイルの既定の場所を表示または変更する  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックして **[プロパティ]** をクリックします。  
  
2.  その [プロパティ] ページの左側のパネルで、**[データベースの設定]** タブをクリックします。  
  
3.  **[データベースの既定の場所]**パネルに、新しいデータ ファイルと新しいログ ファイルの現在の既定の場所が表示されます。 既定の場所を変更するには、 **[データ]** フィールドまたは **[ログ]** フィールドに新しい既定のパス名を入力するか、参照ボタンをクリックしてパス名を選択します。  
  
>**注:** 既定の場所を変更したら、SQLServer サービスをいったん停止してから再起動して変更を完了する必要があります。  
  
## 参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [データベースの作成](../../relational-databases/databases/create-a-database.md)  
  
  