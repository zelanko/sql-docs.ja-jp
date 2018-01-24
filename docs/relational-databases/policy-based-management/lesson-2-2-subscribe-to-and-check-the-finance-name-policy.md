---
title: "Finance の名前ポリシーのサブスクライブおよび確認 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 126b4c4c-2a1c-4701-a0ad-8de23fbd7306
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 247af1bcdb8e3d3293792fb52a5d0e8149ce6ccc
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="lesson-2-2---subscribe-to-and-check-the-finance-name-policy"></a>レッスン 2-2 - Finance の名前ポリシーのサブスクライブおよび確認
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] ここでは、Finance データベースを構成し、Finance ポリシー カテゴリをサブスクライブします。 その後で、Finance の名前ポリシーをテストします。  
  
### <a name="to-subscribe-to-the-finance-policy-category"></a>Finance ポリシー カテゴリをサブスクライブするには  
  
1.  オブジェクト エクスプローラーで **[データベース]**を展開し、 **[Finance]**を右クリックして、 **[ポリシー]**をポイントし、 **[カテゴリ]**をクリックします。  
  
2.  **Finance** カテゴリの **[サブスクライブ済み]** チェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-test-the-enforcement-of-the-finance-name-policy"></a>Finance の名前ポリシーの適用をテストするには  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でクエリ ウィンドウを開きます。 **Finance の名前** ポリシーに違反するテーブルの作成を試みる次のステートメントを実行します。 このテーブルは、テーブル名が文字列 **fintbl**で始まっていないため、ポリシーに違反します。  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
    ポリシーにより、テーブルの作成が防止され、ポリシー名を含む情報メッセージが返されます。  
  
2.  有効な名前を指定するには、コードを次のように変更し、ステートメントを再度実行します。  
  
    ```  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO  
  
    ```  
  
    今度はテーブルが作成されます。  
  
### <a name="to-apply-the-policy-to-the-whole-server"></a>ポリシーをサーバー全体に適用するには  
  
1.  現在、Finance ポリシー カテゴリをサブスクライブするのは Finance データベースだけです。 多くの場合、ポリシー カテゴリをサーバー全体に適用する方が簡単です。 オブジェクト エクスプローラーで **[管理]**を展開し、 **[ポリシー管理]**を右クリックして、 **[カテゴリの管理]**をクリックします。  
  
2.  **[ポリシー カテゴリの管理]** ダイアログ ボックスで Finance カテゴリを探し、Finance カテゴリの **[データベースのサブスクリプションの要求]** チェック ボックスをオンにします。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] これで Finance カテゴリがすべてのデータベースに適用されるようになります。ただし、作成した条件により、Finance の名前ポリシーは Finance データベースにのみ適用されることになります。 これは、条件を複雑に組み合わせることで、多数のサーバーに対して適切な方法でポリシーを適用できるということを示しています。  
  
## <a name="summary"></a>[概要]  
このチュートリアルでは、ポリシー ベースの管理の条件、ポリシー、およびポリシー グループを作成する方法と、フィルターを適用してポリシー ベースの管理対象がポリシーに準拠しているかどうかを調べる方法について学習しました。  
  
## <a name="next"></a>Next  
このチュートリアルはこれで終了です。 最初に戻るには、「 [チュートリアル: ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/tutorial-administering-servers-by-using-policy-based-management.md)」をクリックしてください。  
  
チュートリアルの一覧については、「 [SQL Server 2016 チュートリアル](../../sql-server/tutorials-for-sql-server-2016.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
  
