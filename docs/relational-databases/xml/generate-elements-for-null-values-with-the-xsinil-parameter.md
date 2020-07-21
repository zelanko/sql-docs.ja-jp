---
title: XSINIL を使用した NULL 値に対する要素の生成 | Microsoft Docs
description: ELEMENTS ディレクティブで XSINIL パラメーターを使用して、NULL 値に対して XML 要素を生成する方法について学習します。
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
ms.custom: seo-lt-2019
ms.openlocfilehash: 7cf18eb7c5dea9a61988533205a3a64ab1ae3fd0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85638952"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>XSINIL パラメーターを使用した NULL 値に対する要素の生成

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

**ELEMENTS** ディレクティブにより構成される XML では、各列の値が XML の要素にマップされます。 既定では、列の値が NULL の場合、要素は追加されません。 ただし、ELEMENTS ディレクティブでオプションの **XSINIL** パラメーターを指定することにより、NULL 値に対しても要素を作成するように要求できます。 この場合、値が NULL の各列に対して、TRUE に設定された **xsi:nil** 属性を持つ要素が返されます。  
  
## <a name="see-also"></a>参照

[FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)

[SELECT - FOR 句](../../t-sql/queries/select-for-clause-transact-sql.md)
