---
title: データファイルとログファイルの既定の場所を表示または変更する (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 06d17a4feaec0db614f61fb7761b37ea415efc24
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62808712"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a>データ ファイルとログ ファイルの既定の場所の表示または変更 (SQL Server Management Studio)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、新しいデータ ファイルとログ ファイルの既定の場所を表示および変更する方法について説明します。 既定のパスはレジストリから取得されます。 場所を変更した後は、別の場所が指定されない限り、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで作成されるすべての新しいデータベースに関して、この場所が使用されます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Recommendations (推奨事項)](#Recommendations)  
  
-   **以下を使用してデータ ファイルとログ ファイルの既定の場所を表示または変更するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
-   **補足情報:**  [既定の場所を変更する](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
 データ ファイルとログ ファイルを保護するために、それらがアクセス制御リスト (ACL) によって保護されていることを確認します。 ACL は、ファイルを作成するディレクトリのルートに設定する必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a>データベース ファイルの既定の場所を表示または変更するには  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックして **[プロパティ]** をクリックします。  
  
2.  左側のパネルで、 **[データベースの設定]** ページをクリックします。  
  
3.  
  **[データベースの既定の場所]** パネルに、新しいデータ ファイルと新しいログ ファイルの現在の既定の場所が表示されます。 既定の場所を変更するには、 **[データ]** フィールドまたは **[ログ]** フィールドに新しい既定のパス名を入力するか、参照ボタンをクリックしてパス名を選択します。  
  
##  <a name="FollowUp"></a>補足情報: 既定の場所を変更した後  
 変更を完了するには、SQLServer サービスをいったん停止してから再起動する必要があります。  
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-sql&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [データベースの作成](../../relational-databases/databases/create-a-database.md)  
  
  
