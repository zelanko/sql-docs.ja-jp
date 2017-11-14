---
title: "DCOM で実行するように、DLL の有効化 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e2d67a595c97547934b04794f036d58445e8c282
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="enabling-a-dll-to-run-on-dcom"></a>DCOM 上で実行する DLL を有効にします。
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 次の手順では、DCOM とコンポーネント サービスを介して Microsoft インターネット インフォメーション サービス (HTTP) の両方を使用するビジネス オブジェクト .dll を有効にする方法を説明します。  
  
1.  コンポーネント サービス MMC スナップインで新しい空のパッケージを作成します。  
  
     コンポーネント サービス MMC スナップインで使用するパッケージを作成し、このパッケージに DLL を追加します。 これにより、.dll ファイルは、DCOM、経由でアクセスできるが、IIS を介してユーザー補助機能が削除されます。 (.Dll、レジストリでチェックする場合、 **Inproc**キーは空ですこのトピックでは、後半で説明されている、アクティベーション属性を設定の値を追加、 **Inproc**キーです。)。  
  
2.  パッケージにビジネス オブジェクトをインストールします。  
  
     -または-  
  
     インポート、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)オブジェクトをパッケージにします。  
  
3.  パッケージのアクティベーション属性を設定**作成者のプロセスで**(ライブラリ アプリケーション)。  
  
     .Dll を DCOM と IIS を介して、同じコンピューター上でアクセス可能にするには、コンポーネント サービス MMC スナップインで、コンポーネントのアクティベーション属性を設定する必要があります。 属性を設定した後**作成者のプロセスで**、表示になります、 **Inproc**コンポーネント サービスへのポインターが .dll をサロゲート サーバーのレジストリ キーが追加されました。  
  
 コンポーネント サービス (または Microsoft トランザクション サービス、Windows NT を使用している場合) の詳細については、および方法を次の手順を実行し、Microsoft Transaction Server Web サイトを参照してください。



