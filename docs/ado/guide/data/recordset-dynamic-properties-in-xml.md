---
title: XML でのレコード セットの動的プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset dynamic properties in XML [ADO]
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50841931d26847ba339d64634d3eff4d7a7efc1b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712546"
---
# <a name="recordset-dynamic-properties-in-xml"></a>XML でのレコードセットの動的プロパティ
(クライアント カーソル エンジン) から次のレコード セット プロバイダー固有のプロパティは、現在 XML 形式に永続化されます。  
  
-   更新プログラムの再同期  
  
-   一意テーブル  
  
-   一意のスキーマ  
  
-   一意のカタログ  
  
-   再同期コマンド  
  
-   IRowsetChange  
  
-   IRowsetUpdate  
  
-   CommandTimeOut  
  
-   BatchSize  
  
-   UpdateCriteria  
  
-   名前を変更します。  
  
-   AutoRecalc  
  
 これらのプロパティは、スキーマのセクションでは永続化されるレコード セットの要素の定義の属性として保存されます。 これらの属性が行セットのスキーマ名前空間で定義され、接頭辞を付ける必要があります"rs:"です。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
