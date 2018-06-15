---
title: XML 内のレコード セットの動的プロパティ |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd874d0db6d026b82ddbc8055a17a073194c6e07
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272331"
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
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
