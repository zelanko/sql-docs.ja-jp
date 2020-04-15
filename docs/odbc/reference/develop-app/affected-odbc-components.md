---
title: 影響を受ける ODBC コンポーネント |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d9155fa1c9df5846f069e93a3db1b969e9219ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306476"
---
# <a name="affected-odbc-components"></a>影響を受ける ODBC コンポーネント
下位互換性は、ドライバー マネージャーの新しいバージョンの導入によってアプリケーション、ドライバー マネージャー、およびドライバーがどのように影響を受ける方法を説明します。 これは、アプリケーションとドライバーのいずれかまたは両方が古いバージョンに残っている場合に影響します。 したがって、次の表に示すように、下位互換性には 3 種類の点を考慮する必要があります。  
  
|Type|DM のバージョン|アプリケーションのバージョン|ドライバのバージョン|  
|----------|-------------------|----------------------------|-----------------------|  
|ドライバ マネージャの下位互換性|*3.x*|*2.x*|*2.x*|  
|ドライバの下位互換性[1]|*3.x*|*2.x*|*3.x*|  
|アプリケーションの下位互換性|*3.x*|*3.x*|*2.x*|  
  
 ドライバの下位互換性については、「付録 G: 下位互換性のためのドライバガイドライン」で主に説明しています。  
  
> [!NOTE]
>  標準に準拠したアプリケーション (たとえば、オープン グループまたは ISO CLI 標準に従って記述されたアプリケーション) は、ODBC *3.x*ドライバー マネージャーを使用して ODBC *3.x*ドライバーを使用して動作することが保証されています。 アプリケーションが使用している機能は、ドライバーで使用できることを前提としています。 また、標準準拠のアプリケーションは、ODBC *3.x*ヘッダー ファイルを使用してコンパイルされているものと見なされます。
