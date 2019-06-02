---
title: XSINIL パラメーターを使用した NULL 値に対する要素の生成 | Microsoft Docs
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f0889de0a7525e0e5a7ea91ba169011aaf4e341a
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175179"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>XSINIL パラメーターを使用した NULL 値に対する要素の生成

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

**ELEMENTS** ディレクティブにより構成される XML では、各列の値が XML の要素にマップされます。 既定では、列の値が NULL の場合、要素は追加されません。 ただし、ELEMENTS ディレクティブでオプションの **XSINIL** パラメーターを指定することにより、NULL 値に対しても要素を作成するように要求できます。 この場合、値が NULL の各列に対して、TRUE に設定された **xsi:nil** 属性を持つ要素が返されます。  
  
## <a name="see-also"></a>参照

[FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)

[SELECT - FOR 句](../../t-sql/queries/select-for-clause-transact-sql.md)
