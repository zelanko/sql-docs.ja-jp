---
title: ODBC コンポーネントの影響を受ける |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], affected components
- application upgrades [ODBC], affected components
- compatibility [ODBC], affected components
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], affected components
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 046ec16827e46f6cdf71881ec2f1b6c908fb42fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910137"
---
# <a name="affected-odbc-components"></a>影響を受ける ODBC コンポーネント
旧バージョンとの互換性は、アプリケーション、ドライバー マネージャー、およびドライバーがドライバー マネージャーの新しいバージョンの導入によって影響を受ける方法について説明します。 アプリケーションの古いバージョンで残っていなくても、これらの両方またはいずれかにはドライバーに影響します。 、そのため、次の 3 つの種類があります旧バージョンとの互換性を考慮すると、次の表に示すようにします。  
  
|型|DM のバージョン|アプリケーションのバージョン|ドライバーのバージョン|  
|----------|-------------------|----------------------------|-----------------------|  
|旧バージョンと互換性のドライバー マネージャー|3 *.x*|2*x。*|2*x。*|  
|[1] のドライバーの旧バージョンとの互換性|3 *.x*|2*x。*|3*x。*|  
|アプリケーションの旧バージョンとの互換性|3*x。*|3*x。*|2*x。*|  
  
 [ドライバーの 1]、旧バージョンとの互換性は旧バージョンとの互換性のため、主に付録 g: ドライバーのガイドラインについて説明します。  
  
> [!NOTE]  
>  標準に準拠したアプリケーション — たとえば、Open Group または ISO CLI 標準に従って書き込まれているアプリケーション、ODBC 3 を使用することが保証 *.x*ドライバーは ODBC 3 *.x*ドライバー マネージャー。 アプリケーションを使用している機能は、ドライバーで使用できることと見なされます。 ODBC 3 で標準に準拠したアプリケーションがコンパイルされていると見なされますも *.x*ヘッダー ファイルです。
