---
title: "ピボット解除変換 |Microsoft ドキュメント"
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
- sql13.dts.designer.unpivottrans.f1
helpviewer_keywords:
- Unpivot transformation
- more normalized data set [Integration Services]
- normalized data [Integration Services]
- datasets [Integration Services], normalized data
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d491bb19b4eb86bd0fe75a7b8ca8e7b6e5d226b5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="unpivot-transformation"></a>ピボット解除変換
  ピボット解除変換は、単一のレコード内にある複数の列の値を、単一の列内で同じ値を持つ複数のレコードに展開することにより、正規化されていないデータセットを正規化されたバージョンに変換します。 たとえば、顧客名を一覧表示するデータセットに、顧客ごとに 1 つの行があり、製品と購入した数量がその行の列に表示されているとします。 ピボット解除変換がこのデータセットを正規化すると、データセットには、顧客が購入した各製品に対して異なる行が含まれるようになります。  
  
 次の図は、データが Product 列でピボット解除される前のデータセットを示しています。  
  
 ![ピボット処理解除後のデータセット](../../../integration-services/data-flow/transformations/media/mw-dts-18.gif "ピボット処理解除後のデータセット")  
  
 次の図は、データが Product 列でピボット解除された後のデータセットを示しています。  
  
 ![ピボット処理は前に、のデータセット](../../../integration-services/data-flow/transformations/media/mw-dts-17.gif "ピボット処理は前に、のデータセット")  
  
 状況によっては、ピボット解除された結果には予期しない値を持つ行が含まれる場合があります。 たとえば、図に示したサンプル データのピボット解除では、Fred のすべての Qty 列が NULL 値である場合、出力に含まれる Fred の行は 5 つではなく 1 つだけです。 Qty 列には、列データ型に応じて、NULL または 0 のいずれかが含まれます。  
  
## <a name="configuration-of-the-unpivot-transformation"></a>ピボット解除変換の構成  
 ピボット解除変換には、 **PivotKeyValue** カスタム プロパティがあります。 このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。 詳細については、「[Integration Services &#40;SSIS&#41; の式](../../../integration-services/expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../../integration-services/expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)」を参照してください。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はありません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[ピボット解除変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[ピボット解除変換エディター]](../../../integration-services/data-flow/transformations/unpivot-transformation-editor.md)  
  
 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 データ フロー コンポーネントのプロパティの設定方法については、「 [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  
