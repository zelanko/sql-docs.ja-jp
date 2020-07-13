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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4baacc48beffda2d83a23ce24d3a31c314da5841
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760828"
---
# <a name="static-cursors"></a>静的カーソル
静的カーソルは、カーソルが最初に開かれたときと同じように、常に結果セットを表示します。 実装によっては、静的カーソルは読み取り専用または読み取り/書き込みのいずれかになり、前方スクロールと後方スクロールが提供されます。 通常、静的カーソルは、カーソルを開いた後に、結果セットのメンバーシップ、順序、または値に対して行われた変更を検出しません。 静的カーソルは、それ自体の更新、削除、挿入を検出してもかまいませんが、必ず行う必要はありません。  
  
 静的カーソルは、他の更新、削除、および挿入を検出しません。 たとえば、静的カーソルが行をフェッチした後で、別のアプリケーションによってその行が更新されるものとします。 アプリケーションで静的カーソルから行を再フェッチした場合、他のアプリケーションによって変更が行われたにも関わらず、認識される値は変更されていません。 すべての種類のスクロールがサポートされていますが、プロバイダーがブックマークをサポートする場合とサポートしていない場合があります。  
  
 アプリケーションでデータの変更を検出する必要がなく、スクロールが必要な場合は、静的カーソルが最適な選択肢です。 **Adopenstatic Cursor Typeenum**を使用して、ADO で静的カーソルを使用することを指定します。  
  
## <a name="see-also"></a>参照  
 [順方向専用カーソル](../../../ado/guide/data/forward-only-cursors.md)   
 [キーセットカーソル](../../../ado/guide/data/keyset-cursors.md)   
 [動的カーソル](../../../ado/guide/data/dynamic-cursors.md)
