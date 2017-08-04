---
title: "行サンプリング変換エディター (サンプリング ページ) |Microsoft ドキュメント"
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
- sql13.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql13.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1c55e2136e1ca72ec840f09b723001045bbec445
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="row-sampling-transformation-editor-sampling-page"></a>行サンプリング変換エディター ([サンプリング] ページ)
  **[行サンプリング変換エディター]** ダイアログ ボックスを使用すると、指定された行数を使用して、入力の一部をサンプルに分割できます。 この変換は、入力を 2 つの別個の出力に分割します。  
  
 行サンプリング変換の詳細については、「 [Row Sampling Transformation](../../../integration-services/data-flow/transformations/row-sampling-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[行数]**  
 サンプルとして使用する入力における行数を指定します。  
  
 このプロパティの値は、プロパティ式を使用して指定することができます。  
  
 **[サンプル出力名]**  
 サンプリングされた行を含める出力の一意な名前を指定します。 指定した名前は、SSIS デザイナー内に表示されます。  
  
 **[選択されていない出力名]**  
 サンプリングから除外された行を含む出力の一意な名前を指定します。 指定した名前は、SSIS デザイナー内に表示されます。  
  
 **[次のランダム シードを使用する]**  
 変換でサンプルを作成するために使用する乱数ジェネレーターのサンプリング シードを指定します。 このオプションは、開発およびテスト用にのみ使用することをお勧めします。 ランダム シードを指定しなかった場合は、Microsoft Windows のティック数がシードとして使用されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [比率サンプリング変換](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)  
  
  
