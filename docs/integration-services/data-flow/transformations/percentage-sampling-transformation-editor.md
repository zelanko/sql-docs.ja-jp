---
title: "比率サンプリング変換エディター |Microsoft ドキュメント"
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
- sql13.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a3cf0dd802330585e50428b3301270930b31766d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="percentage-sampling-transformation-editor"></a>比率サンプリング変換エディター
  **[比率サンプリング変換エディター]** ダイアログ ボックスを使用すると、指定された行の割合を使用して、入力の一部をサンプルに分割できます。 この変換は、入力を 2 つの別個の出力に分割します。  
  
 比率サンプリング変換の詳細については、「 [Percentage Sampling Transformation](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[行の割合]**  
 サンプルとして使用する入力における行の割合を指定します。  
  
 このプロパティの値は、プロパティ式を使用して指定することができます。  
  
 **[サンプル出力名]**  
 サンプリングされた行を含める出力の一意な名前を指定します。 指定された名前は、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーに表示されます。  
  
 **[選択されていない出力名]**  
 サンプリングから除外された行を含む出力の一意な名前を指定します。 指定された名前は、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーに表示されます。  
  
 **[次のランダム シードを使用する]**  
 変換でサンプルを作成するために使用する乱数ジェネレーターのサンプリング シードを指定します。 このオプションは、開発およびテスト用にのみ使用することをお勧めします。 ランダム シードが指定されない場合は、Microsoft Windows のティック数が使用されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [行サンプリング変換](../../../integration-services/data-flow/transformations/row-sampling-transformation.md)  
  
  
