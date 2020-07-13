---
title: 列コピー変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fd2745070a92ab71e89f3bfa9edd8673b676632b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430889"
---
# <a name="copy-column-transformation"></a>列コピー変換
  列コピー変換は、入力列をコピーして新しい列を変換出力に追加し、新しい列を作成します。 後のデータ フローで、その列コピーに別の変換を適用できます。 たとえば、列コピー変換を使用して列のコピーを作成した後、文字マップ変換を使用してそのコピーしたデータを大文字に変換したり、集計変換を使用して新しい列に集計を適用したりできます。  
  
## <a name="configuration-of-the-copy-column-transformation"></a>列コピー変換の構成  
 列コピー変換を構成するには、コピーする入力列を指定します。 一度の操作で、1 列の複数コピー、または複数列の複数コピーを作成できます。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[列コピー変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [列コピー変換エディター](../../copy-column-transformation-editor.md)」を参照してください。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../../common-properties.md)  
  
-   [変換のカスタム プロパティ](transformation-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [データフロー](../data-flow.md)   
 [Integration Services の変換](integration-services-transformations.md)  
  
  
