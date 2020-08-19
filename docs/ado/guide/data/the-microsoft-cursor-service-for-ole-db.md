---
description: OLE DB 向けの Microsoft カーソル サービス
title: Microsoft Cursor Service for OLE DB |Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f3646ec86f76fcba2f6b82759a4784de7d463279
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452744"
---
# <a name="the-microsoft-cursor-service-for-ole-db"></a>OLE DB 向けの Microsoft カーソル サービス
クライアント側のカーソルを選択するか、 **Cursor location** プロパティを **adUseClient**に設定すると、Microsoft cursor Service for OLE DB が呼び出されます。 また、"クライアントカーソルエンジン" への参照が表示される場合もあります。これは、基本的には ADO のコンテキストでも同じです。 このサービスは、データプロバイダーのカーソルサポート機能を補完します。 その結果、すべてのデータプロバイダーから比較的一様な機能を認識できます。  
  
 OLE DB 用の Cursor Service を使用すると、動的プロパティを使用できるようになり、特定のメソッドの動作が拡張されます。 たとえば、"動的に **最適化** " プロパティを使用すると、 **Find** メソッドなどの特定の操作を容易にするために一時インデックスを作成できます。  
  
 カーソルサービスにより、すべての場合にバッチ更新がサポートされます。 また、静的カーソルなど、データプロバイダーが使用できるカーソルの数が少ない場合に、動的カーソルなど、より多くの機能を持つカーソルの種類をシミュレートします。  
  
## <a name="see-also"></a>参照  
 [OLE DB 用 Microsoft Cursor Service (ADO サービスコンポーネント)](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)
