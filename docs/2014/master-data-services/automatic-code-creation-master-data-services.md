---
title: コードの自動作成 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7159085aacfe569af079c9f7c457a460df960189
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077116"
---
# <a name="automatic-code-creation-master-data-services"></a>コードの自動作成 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、Code 属性の数値または他の数値属性の数値を自動的に生成できます。 コードを自動生成するときは、コードに他の値を入力してもかまいません。正確には、初期値が自動的に設定されます。  
  
## <a name="generating-code-values"></a>コード値の生成  
 管理者は、関連付けられているエンティティのプロパティを編集することによって、Code 属性の値の自動生成を構成できます。 初期値を指定でき、後続の各値は 1 ずつ増分されます。  
  
 いずれかのツールで、またはステージング処理を使用してコード値を MDS に入力するとき、コード値をブランクのままにすると、コード値が自動的に生成されます。 または、自分で選択したコード値を指定することもできます。  
  
## <a name="generating-other-attribute-values"></a>他の属性値の生成  
 管理者は、ビジネス ルールを作成することによって、Code 以外の属性値を自動的に生成できます。 初期値を指定できるだけでなく、後続の各値での増分値も指定できます。  
  
 いずれかのツールで、またはステージング処理を使用して属性値を MDS に入力するとき、属性値をブランクのままにできます。 ビジネス ルールが適用されると、既存の最高の値に基づいて値が増分されます。 たとえば、ルールが "1 から開始して 4 ずつ増加する生成値に対する既定の属性" であり、属性の現在最も高い値が 700 である場合、追加される次のメンバーの値は 704 になります。  
  
## <a name="deleting-automatically-generated-values"></a>自動的に生成される値の削除  
 管理者が Code 属性の値の自動生成を有効にした後、ユーザーが再利用するコード値を持っていたメンバーを誤って削除する場合があります。 "このメンバー コードは、削除されたメンバーによって既に使用されています。" というエラー メッセージが表示されます。 この解決方法には、次の 2 つが挙げられます。  
  
-   **バージョン管理**機能領域で、管理者は、メンバーが削除されたときに発生したトランザクションを取り消すことができます。 ただし、これを行うと、以前のメンバーの属性と階層やコレクションにおけるそのメンバーシップもすべて復元されます。 詳細については、次を参照してください。[トランザクションを破棄する&#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md)です。  
  
-   管理者は、ステージング処理を使用して、メンバーを完全に削除できます。 詳細については、次を参照してください。[非アクティブ化またはステージング処理を使用してメンバーの削除&#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md)です。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|Code 属性の値を自動的に生成します。|[Code 属性の値を自動的に生成&#40;マスター データ サービス&#41;](../../2014/master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|他の属性の値を自動的に生成します。|[Code 以外の属性の値を自動的に生成&#40;マスター データ サービス&#41;](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>関連コンテンツ  
  
-   [マスター データ サービス概要](master-data-services-overview-mds.md)  
  
-   [ビジネス ルール (マスター データ サービス)](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [エンティティ (マスター データ サービス)](../../2014/master-data-services/entities-master-data-services.md)  
  
  