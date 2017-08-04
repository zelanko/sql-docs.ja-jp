---
title: "マルチキャスト変換 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8619a0ed02ffc73126eb151f4a83a0b6b24c4be8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="multicast-transformation"></a>マルチキャスト変換
  マルチキャスト変換は、入力を 1 つ以上の出力に配信します。 この変換は条件分割変換と似ています。 いずれの変換も、1 つの入力を複数の出力に送信します。 この 2 つの変換の違いは、マルチキャスト変換は各行を各出力に送信するのに対し、条件分割変換は 1 行を単一の出力に送信する点です。 詳細については、「 [Conditional Split Transformation](../../../integration-services/data-flow/transformations/conditional-split-transformation.md)」を参照してください。  
  
 マルチキャスト変換を構成するには、出力を追加します。  
  
 マルチキャスト変換を使用すると、パッケージはデータの論理コピーを作成できます。 この機能は、パッケージで複数の変換セットを同一のデータに適用する必要がある場合に役に立ちます。 たとえば、データの 1 つのコピーを集計して要約情報のみを変換先で読み込み、そのデータのもう 1 つのコピーを参照値と派生列で拡張し、その後変換先で読み込みます。  
  
 この変換は 1 つの入力と複数の出力をとります。 エラー出力はサポートされていません。  
  
## <a name="configuration-of-the-multicast-transformation"></a>マルチキャスト変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[マルチキャスト変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [マルチキャスト変換エディター](../../../integration-services/data-flow/transformations/multicast-transformation-editor.md)」を参照してください。  
  
 プログラムによって設定できるプロパティの詳細については、「 [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)」を参照してください。  
  
## <a name="related-tasks"></a>関連タスク  
 このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ フロー](../../../integration-services/data-flow/data-flow.md)   
 [Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
