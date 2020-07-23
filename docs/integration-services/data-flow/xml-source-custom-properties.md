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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d9d64d5b477ff31334bc6b60b88e1bbb01811d8d
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920308"
---
# <a name="xml-source-custom-properties"></a>XML 入力元のカスタム プロパティ

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  XML ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、XML ソースのカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|AccessMode|整数|XML データへのアクセスに使用するモード。|  
|UseInlineSchema|Boolean|XML ソース内のインライン スキーマ定義を使用するかどうかを示す値。 このプロパティの既定値は **False**です。|  
|XMLData|String|XML データを取得するファイルまたは変数。<br /><br /> このプロパティの値は、プロパティ式を使用して指定することができます。|  
|XMLSchemaDefinition|String|スキーマ定義ファイル (.xsd) のパスおよびファイル名。<br /><br /> このプロパティの値は、プロパティ式を使用して指定することができます。|  
  
 次の表は、XML ソースの出力のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|説明|  
|-------------------|---------------|-----------------|  
|RowsetID|String|出力に関連付けられた行セットを識別する値。|  
  
 XML ソースの出力列には、カスタム プロパティがありません。  
  
 詳細については、「 [XML ソース](../../integration-services/data-flow/xml-source.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
