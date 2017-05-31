---
title: "XML 形式での実行プランの保存 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5e60ae53c74f8f6df450ac6abc5a421f773ce434
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="save-an-execution-plan-in-xml-format"></a>XML 形式での実行プランの保存
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用すると、実行プランを XML ファイルとして保存し、開いて参照することができます。  
  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の実行プラン機能または XML プラン表示 SET オプションを使用するには、実行プランを生成する [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリを実行するための適切な権限と、クエリが参照するすべてのデータベースに対する SHOWPLAN 権限が必要です。  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a>XML 表示プラン SET オプションを使用してクエリ プランを表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でクエリ エディターを開き、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  次のステートメントを使用して、SHOWPLAN_XML を有効にします。  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     次のステートメントを使用して、STATISTICS XML を有効にします。  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     SHOWPLAN_XML は、クエリのコンパイル時クエリ実行プラン情報を生成しますが、クエリの実行は行いません。 STATISTICS XML は、クエリの実行時クエリ実行プラン情報を生成し、クエリを実行します。  
  
3.  クエリを実行します。 例:  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  **[結果]** ペインで、クエリ プランを含む **[Microsoft SQL Server XML Showplan]** を右クリックし、 **[結果に名前を付けて保存]**をクリックします。  
  
5.  **[**\<グリッドまたはテキスト> **の結果を保存]** ダイアログ ボックスで、**[保存の種類]** ボックスの **[すべてのファイル (\*.\*)]** をクリックします。  
  
6.  **[ファイル名]** ボックスに \<name**>.sqlplan** の形式で名前を入力し、**[保存]** をクリックします。  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a>SQL Server Management Studio のオプションを使用して実行プランを保存するには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、推定実行プランまたは実際の実行プランを生成します。 詳細については、「 [推定実行プランの表示](../../relational-databases/performance/display-the-estimated-execution-plan.md) 」または「 [実際の実行プランの表示](../../relational-databases/performance/display-an-actual-execution-plan.md)」を参照してください。  
  
2.  結果ペインの **[実行プラン]** タブで、グラフィカルな実行プランを右クリックし、 **[実行プランに名前を付けて保存]**をクリックします。  
  
     代わりに、**[ファイル]** メニューの **[実行プランに名前を付けて保存]** をクリックしてもかまいません。  
  
3.  **[名前を付けて保存]** ダイアログ ボックスで、**[ファイルの種類]** が **[実行プラン ファイル (\*.sqlplan)]** に設定されていることを確認します。  
  
4.  **[ファイル名]** ボックスに \<name**>.sqlplan** の形式で名前を入力し、**[保存]** をクリックします。  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a>保存した XML クエリ プランを SQL Server Management Studio で開くには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で **[ファイル]** メニューの **[開く]** をポイントし、**[ファイル]** をクリックします。  
  
2.  **[ファイルを開く]** ダイアログ ボックスで **[ファイルの種類]** を **[実行プラン ファイル (\*.sqlplan)]** に設定し、保存済みの XML クエリ プラン ファイルだけを表示します。  
  
3.  表示する XML クエリ プラン ファイルを選択し、**[開く]** をクリックします。  
  
     代わりに、Windows エクスプローラーで、拡張子が **.sqlplan**のファイルをダブルクリックしてもかまいません。 プランが、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で開かれます。  
  
## <a name="see-also"></a>参照  
 [SET SHOWPLAN_XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-showplan-xml-transact-sql.md)   
 [SET STATISTICS XML &#40;Transact-SQL&#41;](../../t-sql/statements/set-statistics-xml-transact-sql.md)  
  
  
