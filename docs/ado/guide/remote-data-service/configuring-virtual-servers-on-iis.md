---
description: IIS での仮想サーバーの構成
title: IIS での仮想サーバーの構成 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
author: rothja
ms.author: jroth
ms.openlocfilehash: 3a537ed684fb3f39d89af8c7f95d4e2f1abdb140
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759859"
---
# <a name="configuring-virtual-servers-on-iis"></a>IIS での仮想サーバーの構成
インターネットインフォメーションサービス4.0 で仮想サーバーを作成する場合は、RDS を使用するように仮想サーバーを構成するために、次の2つの追加の手順が必要になります。  
  
1.  サーバーをセットアップするときに、[実行アクセスを許可する] チェックボックスをオンにします。  
  
2.  msadcs.dll を *vroot*\ msadc に移動します。 *vroot* は仮想サーバーのホームディレクトリです。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および [Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416) 」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [RDS の基礎](./rds-fundamentals.md)