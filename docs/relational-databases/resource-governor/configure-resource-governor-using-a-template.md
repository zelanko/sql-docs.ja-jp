---
title: "テンプレートを使用したリソース ガバナーの構成 | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: resource-governor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: df7896e10efd804a93ea6ef76254df60c3845e67
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="configure-resource-governor-using-a-template"></a>テンプレートを使用してリソース ガバナーを構成する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] に用意されているテンプレートを使用して Resource Governor を構成できます。  
  
-   **作業を開始する準備:**  [アクセス許可](#Permissions)  
  
-   **ワークロード グループの作成に使用するもの:**  [テンプレート](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
 次の手順に従って、リソース プールおよびそのプールのワークロード グループを作成するテンプレートを開いて変更します。 また、このテンプレートを使用すると、既定のグループまたは作成したワークロード グループへの新しい接続をルーティングするための、ユーザー定義の分類子関数を作成できます。  
  
###  <a name="Permissions"></a> Permissions  
 テンプレートでリソース ガバナーの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するには、CONTROL SERVER 権限が必要です。  
  
##  <a name="ConfRGTemplate"></a> テンプレートを使用してリソース ガバナーを構成する  
 **のテンプレートを使用してリソース ガバナーを構成するには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]**をクリックします。  
  
2.  **テンプレート エクスプローラー**で、 **[リソース ガバナー]**を展開して、 **[リソース ガバナーの構成]**をダブルクリックします。  
  
3.  **[データベース エンジンへの接続]**で、必要な情報を入力し、 **[OK]**をクリックします。 テンプレート Configure Resource Governor.sql がクエリ エディターに示されます。 このテンプレートを使用して、リソース プール、ワークロード グループ、および分類子関数を構成します。  
  
4.  テンプレートの値を変更するには、Ctrl キーと Shift キーを押しながら M キーを押します。 **[テンプレート パラメーターの値の指定]** ウィンドウで、使用する値を入力します。  
  
5.  テンプレートに加えた変更を保存するには、 **[OK]**をクリックします。  
  
6.  クエリを実行するには、 **[実行]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [[リソース ガバナー]](../../relational-databases/resource-governor/resource-governor.md)   
 [リソース ガバナーの有効化](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [リソース ガバナー リソース プール](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [リソース ガバナー ワークロード グループ](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [リソース ガバナーの分類子関数](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [リソース ガバナー プロパティの表示](../../relational-databases/resource-governor/view-resource-governor-properties.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
