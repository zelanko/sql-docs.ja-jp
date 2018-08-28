---
title: 列の既定値の指定 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], defaults
- default values
ms.assetid: 64514aed-b846-407b-992e-cf813f9a1a91
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6d20700c29979d2fdefd79acb5e017258d497861
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43070615"
---
# <a name="specify-default-values-for-columns"></a>列の既定値の指定
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して列に入力される既定値を指定できます。 既定値を割り当てなかった場合、ユーザーが列に何も入力しないと、次のようになります。  
  
-   NULL 値を許可するオプションを設定している場合は、列に NULL が挿入されます。  
  
-   NULL 値を許可するオプションを設定していない場合は、列が空白のままになります。ただし、列に値を指定しないと、行を保存できません。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **既定値を指定する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   バインドされた既定値 (かっこなしで表示されている値) を **[既定値]** フィールドに入力した値で置き換える場合は、既定値のバインドを解除し、新しい既定値で置き換えるかどうかを確認するメッセージが表示されます。  
  
-   文字列を入力するには、値を単一引用符 (') で囲みます。二重引用符 (") では囲まないでください。二重引用符は、二重引用符で囲む必要がある識別子のために予約されています。  
  
-   数値の既定値を入力するには、引用符で囲まずに番号を入力します。  
  
-   オブジェクトまたは関数を入力するには、引用符で囲まずにオブジェクト名または関数名を入力します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>列の既定値を指定するには  
  
1.  **オブジェクト エクスプローラー**で、有効桁数を変更する列が含まれているテーブルを右クリックし、 **[デザイン]** をクリックします。  
  
2.  既定値を指定する列を選択します。  
  
3.  **[列のプロパティ]** タブで、 **[既定値またはバインド]** プロパティに新たな既定値を入力します。  
  
    > [!NOTE]  
    >  数値の既定値を入力するには、数値を入力します。 オブジェクトまたは関数の場合は、その名前を入力します。 英数字の場合は、その値を単一引用符で囲んで入力します。  
  
4.  **[ファイル]** メニューの *[<テーブル名> を保存]* をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-specify-a-default-value-for-a-column"></a>列の既定値を指定するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    CREATE TABLE dbo.doc_exz ( column_a INT, column_b INT) ;  
    GO  
    INSERT INTO dbo.doc_exz (column_a)VALUES ( 7 ) ;  
    GO  
    ALTER TABLE dbo.doc_exz  
    ADD CONSTRAINT col_b_def  
    DEFAULT 50 FOR column_b ;  
    GO  
  
    ```  
  
 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
###  <a name="TsqlExample"></a>  
