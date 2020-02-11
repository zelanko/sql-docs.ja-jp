---
title: テンプレートを使用したリソース ガバナーの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3da27154a824433d214dc495bf7f236ff104274f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68198932"
---
# <a name="configure-resource-governor-using-a-template"></a>テンプレートを使用してリソース ガバナーを構成する
  
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に用意されているテンプレートを使用してリソース ガバナーを構成できます。  
  
-   **作業を開始する準備:**  [アクセス許可](#Permissions)  
  
-   **ワークロードグループを作成するために使用するもの:**  [テンプレート](#ConfRGTemplate)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
 次の手順に従って、リソース プールおよびそのプールのワークロード グループを作成するテンプレートを開いて変更します。 また、このテンプレートを使用すると、既定のグループまたは作成したワークロード グループへの新しい接続をルーティングするための、ユーザー定義の分類子関数を作成できます。  
  
###  <a name="Permissions"></a> Permissions  
 テンプレートでリソース ガバナーの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するには、CONTROL SERVER 権限が必要です。  
  
##  <a name="ConfRGTemplate"></a>テンプレートを使用して Resource Governor を構成する  
 **でテンプレートを使用してリソースガバナーを構成するには[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
1.  
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  
  **テンプレート エクスプローラー**で、 **[リソース ガバナー]** を展開して、 **[リソース ガバナーの構成]** をダブルクリックします。  
  
3.  
  **[データベース エンジンへの接続]** で、必要な情報を入力し、 **[OK]** をクリックします。 テンプレート Configure Resource Governor.sql がクエリ エディターに示されます。 このテンプレートを使用して、リソース プール、ワークロード グループ、および分類子関数を構成します。  
  
4.  テンプレートの値を変更するには、Ctrl キーと Shift キーを押しながら M キーを押します。 
  **[テンプレート パラメーターの値の指定]** ウィンドウで、使用する値を入力します。  
  
5.  テンプレートに加えた変更を保存するには、 **[OK]** をクリックします。  
  
6.  クエリを実行するには、 **[実行]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Resource Governor](resource-governor.md)   
 [Resource Governor を有効にする](enable-resource-governor.md)   
 [リソースプールの Resource Governor](resource-governor-resource-pool.md)   
 [ワークロードグループの Resource Governor](resource-governor-workload-group.md)   
 [Resource Governor 分類子関数](resource-governor-classifier-function.md)   
 [Resource Governor のプロパティの表示](view-resource-governor-properties.md)   
 [Transact-sql&#41;&#40;リソースプールの作成](/sql/t-sql/statements/create-resource-pool-transact-sql)   
 [Transact-sql&#41;&#40;ワークロードグループを作成する](/sql/t-sql/statements/create-workload-group-transact-sql)   
 [CREATE FUNCTION &#40;Transact-sql&#41;](/sql/t-sql/statements/create-function-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
