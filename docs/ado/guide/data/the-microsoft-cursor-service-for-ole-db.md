---
title: "OLE DB 用の Microsoft カーソル サービス |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 53d49e5214be1a91cf5f97cf71387a97f4527a41
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>OLE DB 用の Microsoft カーソル サービス
クライアント側のカーソルの選択またはに設定した場合、 **CursorLocation**プロパティを**adUseClient**、OLE DB の Microsoft カーソル サービスを起動します。 「クライアント カーソル エンジン」、ADO のコンテキストでは基本的に同じであるへの参照も表示があります。 このサービスは、データ プロバイダーのカーソル サポート機能を補完します。 その結果、すべてのデータ プロバイダーで比較的一定な機能を得ることができます。  
  
 OLE DB のカーソル サービスは、動的なプロパティを使用できるようにし、特定のメソッドの動作が向上します。 たとえば、**最適化**動的プロパティなど、特定の操作を容易に一時インデックスの作成を使用して、**検索**メソッド。  
  
 カーソル サービスは、常にバッチを更新するためのサポートを有効します。 データ プロバイダーのみを提供する静的カーソルなどの低機能のカーソルと動的カーソルの場合より高機能な種類のカーソルをシミュレートします。  
  
## <a name="see-also"></a>参照  
 [OLE DB (ADO サービス コンポーネント) 用 Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
