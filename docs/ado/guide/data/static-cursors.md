---
title: 静的カーソル |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8815522ee4f9a4221887696a23a201910d7cfad
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654190"
---
# <a name="static-cursors"></a>静的カーソル
静的カーソルは常に、カーソルが最初に開いたときと、結果セットを表示します。 静的カーソルでは、実装によっては、読み取り専用または読み取り/書き込みと前方と後方スクロールを指定します。 静的カーソルでは、メンバーシップ、順序、または、カーソルを開いた後に結果セットの値に加えられた変更は、通常は検出されません。 静的カーソルは、これを行うには不要ですが、独自の更新、削除、および挿入を検出することがあります。  
  
 静的カーソルは、その他の更新、削除、および挿入を検出することはありません。 たとえば、静的カーソルは、行、および他のアプリケーションをフェッチし、行を更新します。 場合は、アプリケーションでは、静的カーソルから行を変わりません、認識値は、その他のアプリケーションによって行われた変更に関係なく、変更ではありません。 すべての種類のスクロールがサポートされますが、プロバイダーの場合がありますまたはブックマークをサポートしていません。  
  
 アプリケーションがデータの変更し、スクロールが必要なを検出する必要がない場合、最適な選択肢は、静的カーソル。 使用して、 **adOpenStatic CursorTypeEnum** ADO では静的カーソルを使用することを指定します。  
  
## <a name="see-also"></a>参照  
 [順方向専用カーソル](../../../ado/guide/data/forward-only-cursors.md)   
 [Keyset カーソル](../../../ado/guide/data/keyset-cursors.md)   
 [動的カーソル](../../../ado/guide/data/dynamic-cursors.md)
