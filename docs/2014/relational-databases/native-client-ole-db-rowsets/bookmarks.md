---
title: ブックマーク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bookmarks [OLE DB]
- SQL Server Native Client OLE DB provider, bookmarks
- rowsets [OLE DB], bookmarks
- OLE DB rowsets, bookmarks
ms.assetid: 7d9076f2-bf9c-452e-b816-70371a0c1644
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4588780932ab408b5e35a2099767c30bcecc1375
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63183645"
---
# <a name="bookmarks"></a>ブックマーク
  ブックマークを使用すると、コンシューマーは行をすばやく返すことができます。 コンシューマーはブックマークの値を基に、行にランダムにアクセスできます。 ブックマーク列は、行セットの列 0 です。 コンシューマーは、バインド構造体の dwFlag フィールド値に DBCOLUMNSINFO_ISBOOKMARK を設定して、その列がブックマークに使用されることを示します。 また、コンシューマーは行セット プロパティ DBPROP_BOOKMARKS に VARIANT_TRUE を設定します。 その結果、行セットに列 0 が存在できるようになります。 **IRowsetLocate::GetRowsAt** メソッドを使用すると、ブックマークからのオフセットで指定された行で始まる行が取り出されます。  
  
## <a name="see-also"></a>参照  
 [行セット](rowsets.md)  
  
  
