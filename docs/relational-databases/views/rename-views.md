---
title: ビューの名前の変更 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
ms.manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fdc46b1d0addad193f5bc09a9bcd60fab9efe027
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62744025"
---
# <a name="rename-views"></a>ビューの名前の変更
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、ビューの名前を変更できます。  
  
> [!WARNING]  
>  ビューの名前を変更すると、そのビューに依存するコードやアプリケーションの実行が失敗する場合があります。 これには、他のビュー、クエリ、ストアド プロシージャ、ユーザー定義関数、およびクライアント アプリケーションが含まれます。 このようなエラーは連鎖するので注意が必要です。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してビューの名前を変更するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報:** [ビューの名を変更した後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
 ビューのすべての依存関係の一覧を取得します。 ビューを参照するすべてのオブジェクト、スクリプト、またはアプリケーションは、ビューの新しい名前を反映するように変更する必要があります。 詳しくは、「 [Get Information About a View](../../relational-databases/views/get-information-about-a-view.md)」をご覧ください。 ビューの名前を変更するのではなく、ビューを削除してから新しい名前で作成し直すことをお勧めします。 ビューを再作成することにより、ビューで参照されているオブジェクトの依存情報が更新されます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 SCHEMA に対する ALTER 権限または OBJECT に対する CONTROL 権限と、データベースの CREATE VIEW 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-rename-a-view"></a>ビューの名前を変更するには  
  
1.  **オブジェクト エクスプローラー**で、名前を変更するビューを含むデータベースを展開します。次に、 **[ビュー]** フォルダーを展開します。  
  
2.  名前を変更するビューを右クリックし、 **[名前の変更]** を選択します。  
  
3.  ビューの新しい名前を入力します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **ビューの名前を変更するには**  
  
 ビューの名前は **sp_rename** を使用して変更できますが、既存のビューを削除した後、新しい名前でビューを再作成することをお勧めします。  
  
 詳細については、「[CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)」および「[DROP VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/drop-view-transact-sql.md)」を参照してください。  
  
##  <a name="FollowUp"></a>補足情報: ビューの名を変更した後  
 ビューの古い名前を参照するすべてのオブジェクト、スクリプト、およびアプリケーションで新しい名前が使用されていることを確認します。  
  
  
