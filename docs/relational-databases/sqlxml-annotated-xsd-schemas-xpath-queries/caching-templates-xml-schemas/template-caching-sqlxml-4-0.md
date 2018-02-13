---
title: "テンプレート キャッシュ (SQLXML 4.0) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 079817f1179d9fca165366fd67b3d4ab79adc01e
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="template-caching-sqlxml-40"></a>テンプレートのキャッシュ (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
テンプレートをキャッシュすると、パフォーマンスが大幅に向上します。 テンプレートのキャッシュを設定している場合、テンプレートは初回実行時にメモリに残るので、 以降のテンプレート実行でパフォーマンスが向上します。  
  
 テンプレートのキャッシュ サイズは、レジストリに次のキーを追加することで設定できます。  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 テンプレートのサイズは、使用できるメモリと使用しているテンプレートの数に基づいて設定します。 既定値は**TemplateCacheSize**サイズは 31 です。 テンプレートのアクセスが遅い場合はキャッシュ サイズを増やし、メモリが少ない場合はキャッシュ サイズを減らします。  
  
 パフォーマンスを向上させることをお勧めを設定すること**TemplateCacheSize**通常使用するテンプレート数よりも大きくします。 場合**TemlateCacheSize**が小さいテンプレートが増えた数として数よりも、テンプレートがある場合、パフォーマンスは低下します。 **TemplateCacheSize** 128 までの値に設定することができます。  
  
 キャッシュされたテンプレートが使用されるときには、毎回テンプレート ファイルの変更回数がチェックされ、更新が必要がどうかが決定されます。 これは、ディスク コピーがキャッシュ コピーより新しいためです。  
  
> [!NOTE]  
>  テンプレートのパラメーターとコマンド プロパティはキャッシュされません。  
  
## <a name="see-also"></a>参照  
 [スキーマのキャッシュ (&) #40 です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)   
 [XSL のキャッシュ (&) #40 です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
