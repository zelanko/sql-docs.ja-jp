---
title: XSL のキャッシュ (SQLXML 4.0) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b95f2970c7d1d9848d6b58c4feaeb462c084d369
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084724"
---
# <a name="xsl-caching-sqlxml-40"></a>XSL のキャッシュ (SQLXML 4.0)
  XSL スタイル シートをキャッシュすると、パフォーマンスが向上します。 XSL のキャッシュを ON に設定している場合、XSL スタイル シートは初回実行時にメモリに残るので、以降の処理でパフォーマンスが向上します。 既定の設定は ON です。  
  
 XSL のキャッシュ サイズは、レジストリに次のキーを追加することで設定できます。  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 XSL のキャッシュ サイズは、使用できるメモリと使用している XSL スタイル シートの数に基づいて設定します。 既定値は**XSLCacheSize**サイズは 31 です。 XSL のアクセスが遅い場合はキャッシュ サイズを増やし、メモリが少ない場合はキャッシュ サイズを減らします。  
  
 パフォーマンスを向上させることをお勧めを設定すること**XSLCacheSize**通常使用する XSL スタイル シートの数よりも高い。 場合**XSLCacheSize**が数よりも小さい XSL スタイル シートのある場合は、XSL スタイル シートがの数と、パフォーマンスが低下します。 **XSLCacheSize** 128 までの値に設定することができます。  
  
 キャッシュされた XSL スタイル シートが使用されるときには、毎回 XSL ファイルの変更回数がチェックされ、更新が必要かどうかが決定されます。 これは、ディスク コピーがキャッシュ コピーより新しいためです。  
  
## <a name="see-also"></a>参照  
 [テンプレートのキャッシュ&#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md)   
 [スキーマのキャッシュ&#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)  
  
  