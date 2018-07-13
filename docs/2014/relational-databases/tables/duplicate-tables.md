---
title: テーブルの複製 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- tables [SQL Server], duplicating
- duplicating tables
- table copying [SQL Server]
ms.assetid: c6b07423-d1e5-4e5e-8681-5088921f5df3
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aacd91d44d5d4939ab699b17d4decc124cffcc30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37198812"
---
# <a name="duplicate-tables"></a>テーブルの複製
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して、新しいテーブルを作成して既存のテーブルから列情報をコピーすることで既存のテーブルを複製できます。  
  
> [!IMPORTANT]  
>  この操作によって複製されるのはテーブルの構造のみです。テーブル行は複製されません。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **テーブルを複製するための方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 対象となるデータベースの CREATE TABLE 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-duplicate-a-table"></a>テーブルを複製するには  
  
1.  テーブルを作成するデータベースに接続していること、およびそのデータベースがオブジェクト エクスプローラーで選択されていることを確認します。  
  
2.  オブジェクト エクスプローラーで、 **[テーブル]** を右クリックし、 **[新しいテーブル]** をクリックします。  
  
3.  オブジェクト エクスプローラーで、コピーするテーブルを右クリックし、 **[デザイン]** をクリックします。  
  
4.  既存のテーブルの列を選択し、 **[編集]** メニューの **[コピー]** をクリックします。  
  
5.  新しいテーブルに戻り、1 行目を選択します。  
  
6.  **[編集]** メニューの **[貼り付け]** をクリックします。  
  
7.  **[ファイル]** メニューの *[<テーブル名> を保存]* をクリックします。  
  
8.  **[名前の選択]** ダイアログ ボックスで、新しいテーブルの名前を入力し、 **[OK]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-duplicate-a-table-in-query-editor"></a>クエリ エディターでテーブルを複製するには  
  
1.  テーブルを作成するデータベースに接続していること、およびそのデータベースがオブジェクト エクスプローラーで選択されていることを確認します。  
  
2.  複製するテーブルを右クリックし、 **[テーブルをスクリプト化]** をポイントして、 **[CREATE]** をポイントします。次に、 **[新しいクエリ エディター ウィンドウ]** をクリックします。  
  
3.  テーブルの名前を変更します。  
  
4.  新しいテーブルに必要でない列をすべて削除します。  
  
5.  **[実行]** をクリックします。  
  
  
