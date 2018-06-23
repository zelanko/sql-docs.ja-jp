---
title: 全体結合変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 27547f95d50bd4552e766184f163dcd3b94a3bb8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179149"
---
# <a name="union-all-transformation"></a>全体結合変換
  全体結合変換は、複数の入力を 1 つの出力に結合します。 たとえば、5 つの異なるフラット ファイル ソースからの出力を全体結合変換への入力とし、1 つの出力に結合できます。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 変換入力は、変換出力に 1 つずつ追加されます。行の並べ替えは発生しません。 パッケージで並べ替え出力が必要な場合は、全体結合変換ではなくマージ変換を使用する必要があります。  
  
 全体結合変換に連結した最初の入力が変換出力のソースとなり、これから変換出力が作成されます。 全体結合変換に次に連結した入力の列は、変換出力の列にマップされます。  
  
 入力をマージするには、入力の列を出力の列にマップします。 最低 1 つの入力の列を、各出力列にマップする必要があります。 2 つの列の間のマッピングでは、列のメタデータが一致する必要があります。 たとえば、マップされた列は同じデータ型である必要があります。  
  
 マップされた列に文字列データが含まれ、出力列の長さが入力列の長さよりも短い場合、入力列を含めることができるように、出力列の長さが自動的に調整されます。 出力列にマップされない入力列は、出力列の値が NULL に設定されます。  
  
 この変換は、複数の入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
## <a name="configuration-of-the-union-all-transformation"></a>全体結合変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[全体結合変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [全体結合変換エディター](../../union-all-transformation-editor.md)」を参照してください。  
  
 プログラムによって設定できるプロパティの詳細については、「 [共通プロパティ](../../common-properties.md)」を参照してください。  
  
 プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。  
  
-   [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 [全体結合変換を使用してデータをマージする](union-all-transformation.md)  
  
  