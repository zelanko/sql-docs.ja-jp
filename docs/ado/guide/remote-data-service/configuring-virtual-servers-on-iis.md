---
title: IIS で仮想サーバーの構成 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f11a031189cd184b2ad91430a059a0352c8fc18c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684257"
---
# <a name="configuring-virtual-servers-on-iis"></a>IIS での仮想サーバーの構成
Internet Information Services 4.0 での仮想サーバーを作成するときに、RDS を使用する仮想サーバーを構成するには、次の 2 つの余分な手順が必要です。  
  
1.  サーバーを設定する場合は、「Execute アクセスを許可する」。 を確認してください。  
  
2.  移動する msadcs.dll *vroot*\msadc、場所*vroot* virtual server のホーム ディレクトリは。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)


