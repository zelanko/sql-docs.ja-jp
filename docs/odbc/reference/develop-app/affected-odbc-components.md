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
ms.openlocfilehash: 72e004e6fd41ee74643fc05ec9020e6ac1933e09
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63186250"
---
# <a name="affected-odbc-components"></a>影響を受ける ODBC コンポーネント
旧バージョンとの互換性は、アプリケーション、ドライバー マネージャー、およびドライバーがドライバー マネージャーの新しいバージョンの導入によって影響を受ける方法について説明します。 これによって影響アプリケーションとドライバーは、古いバージョンのいずれかまたはその両方が残っているとします。 そのため、3 種類の旧バージョンとの互換性、考慮すべき次の表に示すように。  
  
|型|DM のバージョン|アプリケーションのバージョン|ドライバーのバージョン|  
|----------|-------------------|----------------------------|-----------------------|  
|ドライバー マネージャーの旧バージョンとの互換性|3 *.x*|2*x。*|2*x。*|  
|[1] のドライバーの下位互換性|3 *.x*|2*x。*|3*x。*|  
|アプリケーションの旧バージョンとの互換性|3*x。*|3*x。*|2*x。*|  
  
 [1] のドライバーの下位互換性については付録 g: で主に説明します。旧バージョンとの互換性のためのガイドラインをドライバーです。  
  
> [!NOTE]
>  標準に準拠したアプリケーション - など、Open Group または ISO CLI 標準に従って、書き込まれたアプリケーションは保証、ODBC 3 を使用する *.x*ドライバーは ODBC 3 *.x*ドライバー マネージャー。 アプリケーションが使用している機能は、ドライバーで使用できることと見なされます。 ODBC 3 標準に準拠したアプリケーションがコンパイルされていると見なされますも *.x*ヘッダー ファイル。
