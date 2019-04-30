---
title: OLE DB 用の Microsoft カーソル サービス |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursor service for ole db [ADO]
- cursors [ADO], cursor service for OLE DB
ms.assetid: 1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e85d6f482b9d206b2ec705a8d890a4e34e5f2252
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63142931"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>OLE DB 向けの Microsoft カーソル サービス
クライアント側のカーソルを選択またはに設定した場合、 **CursorLocation**プロパティを**adUseClient**、OLE DB の Microsoft カーソル サービスを呼び出すことができます。 「クライアント カーソル エンジン」、ADO のコンテキストでは基本的に同じであるへの参照も表示があります。 このサービスは、データ プロバイダーのカーソル サポート機能を補完します。 その結果、すべてのデータ プロバイダーから機能の統一感を得ることができます。  
  
 OLE DB のカーソル サービスは、動的プロパティを使用できるようにし、特定のメソッドの動作の向上します。 たとえば、**最適化**動的プロパティなどの特定の操作を容易に一時インデックスの作成ができるように、**検索**メソッド。  
  
 カーソル サービスを使用すると、常にバッチを更新するためのサポート。 データ プロバイダーが劣るカーソル、静的カーソルなどを指定できますのみときも、dynamic カーソルより高機能な種類のカーソルをシミュレートします。  
  
## <a name="see-also"></a>参照  
 [OLE DB (ADO サービス コンポーネント) の Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
