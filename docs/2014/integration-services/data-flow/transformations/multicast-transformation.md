---
title: マルチキャスト変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b5c0a38c966c89f426a213f302b45c390b77cfe
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437609"
---
# <a name="multicast-transformation"></a>マルチキャスト変換
  マルチキャスト変換は、入力を 1 つ以上の出力に配信します。 この変換は条件分割変換と似ています。 いずれの変換も、1 つの入力を複数の出力に送信します。 この 2 つの変換の違いは、マルチキャスト変換は各行を各出力に送信するのに対し、条件分割変換は 1 行を単一の出力に送信する点です。 詳細については、「 [Conditional Split Transformation](conditional-split-transformation.md)」を参照してください。  
  
 マルチキャスト変換を構成するには、出力を追加します。  
  
 マルチキャスト変換を使用すると、パッケージはデータの論理コピーを作成できます。 この機能は、パッケージで複数の変換セットを同一のデータに適用する必要がある場合に役に立ちます。 たとえば、データの 1 つのコピーを集計して要約情報のみを変換先で読み込み、そのデータのもう 1 つのコピーを参照値と派生列で拡張し、その後変換先で読み込みます。  
  
 この変換は 1 つの入力と複数の出力をとります。 エラー出力はサポートされていません。  
  
## <a name="configuration-of-the-multicast-transformation"></a>マルチキャスト変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[マルチキャスト変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [マルチキャスト変換エディター](../../multicast-transformation-editor.md)」を参照してください。  
  
 プログラムによって設定できるプロパティの詳細については、「 [共通プロパティ](../../common-properties.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
 このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../data-flow.md)   
 [Integration Services の変換](integration-services-transformations.md)  
  
  
