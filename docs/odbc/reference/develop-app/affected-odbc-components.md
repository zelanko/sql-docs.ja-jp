---
title: 影響を受ける ODBC コンポーネント |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], affected components
- application upgrades [ODBC], affected components
- compatibility [ODBC], affected components
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], affected components
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ebe10a73dfbb5436156518b2a3e4d8388cc84b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769350"
---
# <a name="affected-odbc-components"></a>影響を受ける ODBC コンポーネント
旧バージョンとの互換性は、アプリケーション、ドライバー マネージャー、およびドライバーがドライバー マネージャーの新しいバージョンの導入によって影響を受ける方法について説明します。 これによって影響アプリケーションとドライバーは、古いバージョンのいずれかまたはその両方が残っているとします。 そのため、3 種類の旧バージョンとの互換性、考慮すべき次の表に示すように。  
  
|型|DM のバージョン|アプリケーションのバージョン|ドライバーのバージョン|  
|----------|-------------------|----------------------------|-----------------------|  
|ドライバー マネージャーの旧バージョンとの互換性|3 *.x*|2*x。*|2*x。*|  
|[1] のドライバーの下位互換性|3 *.x*|2*x。*|3*x。*|  
|アプリケーションの旧バージョンとの互換性|3*x。*|3*x。*|2*x。*|  
  
 [1] のドライバーの下位互換性は主に付録 g: ドライバーのガイドラインでの旧バージョンとの互換性について説明します。  
  
> [!NOTE]  
>  標準に準拠したアプリケーション-たとえば、Open Group または ISO CLI 標準に従って作成されたアプリケーションなど、ODBC 3 を使用することが保証されます *.x*ドライバーは ODBC 3 *.x*ドライバー マネージャー。 アプリケーションが使用している機能は、ドライバーで使用できることと見なされます。 ODBC 3 標準に準拠したアプリケーションがコンパイルされていると見なされますも *.x*ヘッダー ファイル。
