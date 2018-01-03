---
title: "InternetTimeout プロパティ (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a012318bccd243b7b950e28978769176de745ca
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="internettimeout-property-rds"></a>InternetTimeout プロパティ (RDS)
要求がタイムアウトする前に待機するミリ秒数を示します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**長い**を要求する前にミリ秒数を表す値がタイムアウトになります。  
  
## <a name="remarks"></a>解説  
 このプロパティは、HTTP または HTTPS プロトコルで送信された要求のみに適用されます。  
  
 3 層環境で要求を実行するのに数分をかかります。 このプロパティを使用して、実行時間の長い要求の待機時間を指定します。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataSpace オブジェクト (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)|  
  
## <a name="see-also"></a>参照  
 [InternetTimeout プロパティの例 (VB)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [InternetTimeout プロパティの例 (VC++)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 

