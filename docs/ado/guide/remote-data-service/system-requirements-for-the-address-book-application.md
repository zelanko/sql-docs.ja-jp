---
title: "システム要件、アドレスの予約アプリケーション |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9d182b879a9b99cafb2624613dc05a7416160f47
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="system-requirements-for-the-address-book-application"></a>アドレス帳アプリケーションのシステム要件
アドレス帳のサンプル アプリケーションをセットアップするには、次のソフトウェアとデータベースの要件を満たす必要があります。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="software-requirements"></a>ソフトウェア要件  
 この Web アプリケーションを実行するためのサーバー コンピューターのソフトウェア要件は次のとおりです。  
  
-   Microsoft Windows NT® Server 4.0、Service Pack 3 以降、または Microsoft Windows® 2000 Server。  
  
-   Microsoft インターネット インフォメーション サービス (IIS) バージョン 3.0 以降、Active Server Pages とします。  
  
 この Web アプリケーションを実行するためのクライアント コンピューターのソフトウェア要件は次のとおりです。  
  
-   Microsoft Internet Explorer 4.0 またはそれ以降。  
  
-   Microsoft Windows NT 4.0 ワークステーションまたはサーバー、Windows 2000、または Microsoft Windows 98 です。  
  
## <a name="database-requirements"></a>データベース要件  
 このサンプルを使用するのには、次が必要です。  
  
-   運用上の Microsoft® SQL Server バージョン 6.5 以降のデータベース サーバーを使用しています。  
  
-   データベースを作成し、サンプル データを設定する特権。  
  
-   Enterprise Manager または ISQL ユーティリティ (SQL Server 7.0 での呼び出されたクエリ アナライザー) を介して設定されたデータを検証します。  
  
 特権があるない場合、データベース管理者は、システムおよびアクセス許可をデータベースまたはデータベースを自動的に設定することを設定する必要があります。  
  
## <a name="see-also"></a>参照  
 [アドレス帳の SQL スクリプトを実行します。](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [アドレス帳のサンプル アプリケーションの実行](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


