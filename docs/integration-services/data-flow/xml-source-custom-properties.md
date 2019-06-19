---
title: XML ソースのカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d65cabf9e0dad9e6c3ee5824a59ce33815722042
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65725670"
---
# <a name="xml-source-custom-properties"></a>XML 入力元のカスタム プロパティ

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  XML ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、XML ソースのカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|[説明]|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|XML データへのアクセスに使用するモード。|  
|UseInlineSchema|Boolean|XML ソース内のインライン スキーマ定義を使用するかどうかを示す値。 このプロパティの既定値は **False**です。|  
|XMLData|String|XML データを取得するファイルまたは変数。<br /><br /> このプロパティの値は、プロパティ式を使用して指定することができます。|  
|XMLSchemaDefinition|String|スキーマ定義ファイル (.xsd) のパスおよびファイル名。<br /><br /> このプロパティの値は、プロパティ式を使用して指定することができます。|  
  
 次の表は、XML ソースの出力のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|[説明]|  
|-------------------|---------------|-----------------|  
|RowsetID|String|出力に関連付けられた行セットを識別する値。|  
  
 XML ソースの出力列には、カスタム プロパティがありません。  
  
 詳細については、「 [XML ソース](../../integration-services/data-flow/xml-source.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
