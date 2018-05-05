---
title: コメント (DMX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- comments [DMX]
- Data Mining Extensions [Analysis Services], comments
- double forward slashes
- commenting characters
- text strings [SQL Server]
- remarks [DMX]
- forward slash-asterisk character pairs
- DMX [Analysis Services], comments
- /*...*/ (comment)
- double hyphens
- // (comment)
- -- (comment character)
ms.assetid: 64d10eb5-4fe8-42c6-b387-eff336315e56
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5c4309b2b3aceb51ba17de90cdf33e62653da573
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="comments-dmx"></a>コメント (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  データ マイニング拡張機能 (DMX) でのコメントは、プログラム内のテキスト文字列のコードを[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]は実行されません。 コメントは解説とも呼ばれています。 コメントを使用すると、コードの説明を記述したり、コードの診断の際に DMX ステートメントまたはスクリプトの一部分を一時的に無効化することができます。  
  
 コメントを使用してプログラム コードの説明を記述しておくと、後でコードの維持を簡単に行うことができます。 コメントを使用して、プログラムの名前、コードを作成した開発者の名前、および主なコード変更の日付などの詳細を記録することができます。 また、複雑な計算の説明やプログラム方法の説明を記述することもできます。  
  
 コメントを記述する際の基本的なガイドラインは次のとおりです。  
  
-   コメント内には、すべての英数字や記号を使用することができます。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、コメント内の文字はすべて無視されます。  
  
-   ステートメント内またはスクリプト内のコメント長には制限がありません。 1 行または複数行のコメントを作成できます。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 次の種類のコメント文字をサポートしています。  
  
-   **(二重スラッシュ)。** 実行するコードと同じ行にコメントを記述する、またはコメントのみの行にコメントを記述するには、このコメント文字を使用します。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] コメントの一部として、行の末尾に二重ハイフンの後ろからすべての情報を評価します。 複数行にわたってコメントを記述する場合、すべてのコメント行の先頭に二重スラッシュを使用します。 このコメント文字の詳細については、次を参照してください。[二重スラッシュ&#40;コメント&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)です。  
  
-   **-(二重ハイフン)。** 実行するコードと同じ行にコメントを記述する、またはコメントのみの行にコメントを記述するには、このコメント文字を使用します。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] コメントの一部として、行の末尾に二重ハイフンの後ろからすべての情報を評価します。 複数行にわたってコメントを記述する場合、すべてのコメント行の先頭に二重ハイフンを使用します。 このコメント文字の詳細については、次を参照してください。 [--&#40;コメント&#41; &#40;DMX&#41;概要](../dmx/comment-dmx-summary.md)です。  
  
-   **/\* ...\*/(スラッシュとアスタリスク文字のペア) です。** 実行コードと同じ行にコメントを記述する、コメント専用の行にコメントを記述する、または実行可能コード内にコメントを記述するには、このコメント文字を使用します。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] コメント開始記号からすべてを評価 (/*) にコメント終了記号 (\*/)、コメント部分として。 複数行のコメントを作成するには、コメント文字のペアでコメントを開始 (/\*)、および閉じるコメント文字のペアでコメントの終了 (\*/)。 コメント行ではそれ以外のコメント文字は使用できません。 このコメント文字の詳細については、次を参照してください。[スラッシュ スター&#40;コメント&#41; &#40;DMX&#41;](../dmx/slash-star-comment-dmx.md)です。  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;参照](../dmx/data-mining-extensions-dmx-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; 演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文表記規則](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [データ マイニング拡張機能&#40;DMX&#41;構文要素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)   
 [構造と DMX 予測クエリの使用状況](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [DMX 選択ステートメントについて](../dmx/understanding-the-dmx-select-statement.md)  
  
  
