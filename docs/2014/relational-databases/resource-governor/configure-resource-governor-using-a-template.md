---
title: テンプレートを使用したリソース ガバナーの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ac998eb2ad98705fc9ac72fc69d7fbfb167bb5b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164994"
---
# <a name="configure-resource-governor-using-a-template"></a>テンプレートを使用してリソース ガバナーを構成する
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に用意されているテンプレートを使用してリソース ガバナーを構成できます。  
  
-   **Before you begin:**  [Permissions](#Permissions)  
  
-   **ワークロード グループの作成に使用するもの:**  [テンプレート](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
 次の手順に従って、リソース プールおよびそのプールのワークロード グループを作成するテンプレートを開いて変更します。 また、このテンプレートを使用すると、既定のグループまたは作成したワークロード グループへの新しい接続をルーティングするための、ユーザー定義の分類子関数を作成できます。  
  
###  <a name="Permissions"></a> Permissions  
 テンプレートでリソース ガバナーの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するには、CONTROL SERVER 権限が必要です。  
  
##  <a name="ConfRGTemplate"></a> テンプレートを使用してリソース ガバナーを構成する  
 **のテンプレートを使用してリソース ガバナーを構成するには [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  **テンプレート エクスプローラー**で、 **[リソース ガバナー]** を展開して、 **[リソース ガバナーの構成]** をダブルクリックします。  
  
3.  **[データベース エンジンへの接続]** で、必要な情報を入力し、 **[OK]** をクリックします。 テンプレート Configure Resource Governor.sql がクエリ エディターに示されます。 このテンプレートを使用して、リソース プール、ワークロード グループ、および分類子関数を構成します。  
  
4.  テンプレートの値を変更するには、Ctrl キーと Shift キーを押しながら M キーを押します。 **[テンプレート パラメーターの値の指定]** ウィンドウで、使用する値を入力します。  
  
5.  テンプレートに加えた変更を保存するには、 **[OK]** をクリックします。  
  
6.  クエリを実行するには、 **[実行]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [[リソース ガバナー]](resource-governor.md)   
 [リソース ガバナーの有効化](enable-resource-governor.md)   
 [リソース ガバナー リソース プール](resource-governor-resource-pool.md)   
 [リソース ガバナー ワークロード グループ](resource-governor-workload-group.md)   
 [リソース ガバナーの分類子関数](resource-governor-classifier-function.md)   
 [リソース ガバナー プロパティの表示](view-resource-governor-properties.md)   
 [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
