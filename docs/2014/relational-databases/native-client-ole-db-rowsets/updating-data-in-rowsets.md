---
title: 行セットのデータの更新 |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updating data [SQL Server]
- rowsets [OLE DB], updating data
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, updating data
- SQL Server Native Client OLE DB provider, data updates
- data updates [SQL Server], OLE DB
ms.assetid: 37769b1c-c480-419a-8c54-5cc420bf73db
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a76d76df980297fd0e7b38cc0d7ec65e310c9e46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165552"
---
# <a name="updating-data-in-rowsets"></a>行セット内のデータの更新
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの更新プログラム[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ コンシューマーがそのデータを含む変更可能な行セットを更新するとします。 コンシューマーがいずれかのサポートを要求したときに、可能な行セットが作成された、 **IRowsetChange**または**IRowsetUpdate**インターフェイスです。  
  
 すべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーが変更可能な行セットを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]行セットをサポートするカーソル。 行セット プロパティ DBPROP_LOCKMODE は、カーソルでの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の同時実行制御動作を変更し、更新可能な行セット内の行をフェッチする動作や、その行セット内のデータの整合性に関するエラーを生成する動作を決定します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは前に、または更新後の行の同期をサポートしています。  
  
> [!NOTE]  
>  IRowChange::SetColumns を使用して、行オブジェクトの 1 つ以上の名前付き列の値を設定できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server カーソルでのデータ更新](updating-data-in-sql-server-cursors.md)  
  
-   [行の再同期](updating-data-in-rowsets-resynchronizing-rows.md)  
  
## <a name="see-also"></a>参照  
 [行セット](rowsets.md)  
  
  