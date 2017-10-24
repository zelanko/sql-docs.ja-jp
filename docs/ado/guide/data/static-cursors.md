---
title: "静的カーソル |Microsoft ドキュメント"
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
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fd0ace9aabf10c2b7e5b34d28bd54dbde84cfd0a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="static-cursors"></a>静的カーソル
常に、静的カーソルには、カーソルが最初に開いた時点と、結果セットが表示されます。 実装によって静的カーソルは読み取り専用または読み取り/書き込みと前方と後方スクロールを提供します。 静的カーソルは、メンバーシップ、順序、または、カーソルが開かれた後に結果セットの値に加えられた変更を通常は検出されません。 静的カーソルは、これらは、これを行うには必要ありませんが、独自の更新、削除、および挿入を検出することがあります。  
  
 静的カーソルは、他の更新、削除、および挿入を検出することはありません。 たとえば、静的カーソルは行、および他のアプリケーションをフェッチし、その行を更新します。 場合は、アプリケーションでは、静的カーソルから行を変わりません、その値は変更されず、他のアプリケーションによって行われた変更に関係なく。 スクロールのすべての型はサポートされてがプロバイダーの場合がありますまたはブックマークをサポートしていない可能性があります。  
  
 アプリケーションがデータの変更し、スクロールが必要なを検出する必要がない場合、静的カーソルをお勧めします。 使用して、 **adOpenStatic CursorTypeEnum** ADO では静的カーソルを使用することを示すためにします。  
  
## <a name="see-also"></a>参照  
 [順方向専用カーソル](../../../ado/guide/data/forward-only-cursors.md)   
 [Keyset カーソル](../../../ado/guide/data/keyset-cursors.md)   
 [動的カーソル](../../../ado/guide/data/dynamic-cursors.md)

