---
title: "Windows 2000 で RDS の構成 |Microsoft ドキュメント"
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
- RDS configuration [ADO], Windows 2000
ms.assetid: ef37e858-c05f-4f52-a65f-3ce6037e0d03
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf283b40d32f26b916d87ecf7d6946bf97eea415
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="configuring-rds-on-windows-2000"></a>Windows 2000 で RDS を構成します。
を Windows 2000 にアップグレードした後に正常に機能する rds 問題が発生した場合は、問題のトラブルシューティングをこれらの手順に従います。  
  
1.  World Wide Web 発行サービスが実行されていること最初 Internet Explorer を使用して http:// サーバーに移動することを確認してください。 この方法で Web サーバーにアクセスすることはできません場合は、コマンド プロンプトを開き、"NET 開始 W3SVC"次のコマンドを入力します。  
  
2.  [スタート] メニューで、[実行] を選択します。 Msdfmap.ini を入力し、メモ帳で msdfmap.ini ファイルを開くには、[ok] をクリックします。 [既定の接続] セクションを確認し、アクセス パラメーターは、NOACCESS に設定されている場合は読み取り専用に変更します。  
  
3.  RegEdit ユーティリティを使用して、"HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DataFactory\HandlerInfo"に移動し、確認**HandlerRequired** 0 に設定されていると**DefaultHandler**は""(Null の文字列)。  
  
     **注**レジストリのこのセクションを変更する場合は、停止して、コマンド プロンプトで次のコマンドを入力し、World Wide Web 発行サービスを再起動する必要があります:"NET 停止 W3SVC"および"NET 開始 W3SVC"です。  
  
4.  RegEdit ユーティリティを使用して、レジストリ"HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch"に移動し、という名前のキーがあることを確認**RDSServer.Datafactory**です。 それ以外の場合は、作成します。  
  
5.  インターネット サービス マネージャーを使用して、既定の Web サイトを見つけて MSADC 仮想ルートのプロパティを表示します。 ディレクトリのセキュリティ/IP アドレスおよびドメイン名の制限を検査します。 「アクセスが拒否されました」がオンの場合は、"Granted"を選択します。  
  
 場合は、サーバーを再起動することを確認して変更を最初に、問題を解決するためには表示されません。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。Windows 8 および Windows Server 2012 以降、Windows オペレーティング システムに RDS サーバー コンポーネントは含まれなくです。 RDS を使用するアプリケーションを移行[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="see-also"></a>参照  
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)



