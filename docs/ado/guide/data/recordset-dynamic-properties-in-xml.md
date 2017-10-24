---
title: "XML 内のレコード セットの動的プロパティ |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 62d9b59fc1145e09f89bbe69b8d7b6e561798e70
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="recordset-dynamic-properties-in-xml"></a>XML 内のレコード セットの動的プロパティ
(クライアント カーソル エンジン) から次のレコード セット プロバイダーに固有のプロパティは、現在を XML 形式に永続化されます。  
  
-   更新プログラムの再同期  
  
-   一意テーブル  
  
-   一意なスキーマ  
  
-   固有のカタログ  
  
-   コマンドを再同期します。  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeOut  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   名前の形状変更します。  
  
-   AutoRecalc  
  
 これらのプロパティは、スキーマ」セクションに永続化レコード セットの要素の定義の属性として保存されます。 これらの属性が行セット スキーマ名前空間で定義され、プレフィックスを持つ必要があります"rs:"です。  
  
## <a name="see-also"></a>参照  
 [XML 形式で保持するレコード](../../../ado/guide/data/persisting-records-in-xml-format.md)

