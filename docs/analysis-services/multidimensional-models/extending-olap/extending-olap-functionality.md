---
title: OLAP 機能を拡張 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 06b73c0b9f8b4c2d93bb81762ebec442f94e7198
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021419"
---
# <a name="extending-olap-functionality"></a>OLAP 機能の拡張
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  プログラマは、複数のデータベース アプリケーションで使用および用途変更する必要がある機能を提供するアセンブリ、パーソナル化拡張機能、およびストアド プロシージャを記述して Analysis Services を拡張できます。 アセンブリを使用すると、新しいプロシージャや機能を MDX 言語に追加したり、パーソナル化アドインを使用したりして、多次元モデルの機能を拡張できます。  
  
 ストアド プロシージャを使用すると、外部ルーチンを呼び出すことができます。これにより、一度共通コードを開発して 1 つの場所に格納できるようになるため、Analysis Services データベースの開発および実装が簡単になります。 ストアド プロシージャを使用して、アプリケーションに、MDX のネイティブ機能によって提供されていないビジネス機能を追加できます。  
  
 パーソナル化は、ユーザーごとに異なる動作を提供するためにキューブに追加するカスタム オブジェクトです。 パーソナル化は、キューブのパーマネント オブジェクトではなく、クライアント アプリケーションがユーザーのセッション中に動的に適用するオブジェクトです。 たとえば、データにアクセスしているユーザーに応じて金額値の通貨を変更したり、個別の KPI を提供したり、オンラインで購入する常連の顧客に合わせた提案リストを提供したりできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [パーソナル化による OLAP の拡張](../../../analysis-services/multidimensional-models/extending-olap/extending-olap-through-personalizations.md)  
  
 [Analysis Services のパーソナル化拡張機能](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
 [ストアド プロシージャの定義](../../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
