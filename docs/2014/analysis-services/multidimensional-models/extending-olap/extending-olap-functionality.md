---
title: OLAP 機能を拡張 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 13209bfc3938ffc6ffe4de2118456686f2dcbd5e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173817"
---
# <a name="extending-olap-functionality"></a>OLAP 機能の拡張
  プログラマは、複数のデータベース アプリケーションで使用および用途変更する必要がある機能を提供するアセンブリ、パーソナル化拡張機能、およびストアド プロシージャを記述して Analysis Services を拡張できます。 アセンブリを使用すると、新しいプロシージャや機能を MDX 言語に追加したり、パーソナル化アドインを使用したりして、多次元モデルの機能を拡張できます。  
  
 ストアド プロシージャを使用すると、外部ルーチンを呼び出すことができます。これにより、一度共通コードを開発して 1 つの場所に格納できるようになるため、Analysis Services データベースの開発および実装が簡単になります。 ストアド プロシージャを使用して、アプリケーションに、MDX のネイティブ機能によって提供されていないビジネス機能を追加できます。  
  
 パーソナル化は、ユーザーごとに異なる動作を提供するためにキューブに追加するカスタム オブジェクトです。 パーソナル化は、キューブのパーマネント オブジェクトではなく、クライアント アプリケーションがユーザーのセッション中に動的に適用するオブジェクトです。 たとえば、データにアクセスしているユーザーに応じて金額値の通貨を変更したり、個別の KPI を提供したり、オンラインで購入する常連の顧客に合わせた提案リストを提供したりできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [パーソナル化による OLAP の拡張](extending-olap-through-personalizations.md)  
  
 [Analysis Services のパーソナル化拡張機能](analysis-services-personalization-extensions.md)  
  
 [ストアド プロシージャの定義](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  