---
title: 安全なまたは無制限のモードの DataFactory の構成 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory configuration in RDS [ADO]
ms.assetid: 8ff24805-dc7a-42ae-b600-5bad0e3f51b8
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e3af0bf538b8d2fb774b06644e8089cf201b5fc6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-datafactory-for-safe-or-unrestricted-modes"></a>安全なまたは無制限のモードの DataFactory を構成します。
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 既定では、ADO は"safe"と共にインストール[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)構成します。 RDS サーバー コンポーネントのセーフ モードでは、次の項目が該当することを意味します。  
  
1.  ハンドラーは (これが必須で、レジストリ キーを設定) RDSServer.DataFactory で必要です。  
  
2.  既定のハンドラー、msdfmap.handler が登録されている、安全なハンドラーの一覧で存在し、既定のハンドラーとしてマークされています。  
  
3.  Msdfmap.ini ファイルは、Windows ディレクトリにインストールされます。 RDS 3 階層のモードで使用する前に、必要に応じてこのファイルを構成する必要があります。  
  
 必要に応じて、構成できます無制限**DataFactory**インストールします。 **DataFactory**カスタム ハンドラーせずに直接使用できます。 ユーザーでは、カスタム ハンドラーを接続文字列を変更することによっても使用できますが、必須ではありません。 使用する場合の影響の詳細については、 **RDSServer.DataFactory**オブジェクトを参照してください[RDS アプリケーションのセキュリティで保護する](../../../ado/guide/remote-data-service/securing-rds-applications.md)です。  
  
 安全な構成のハンドラーのレジストリ エントリを設定するには、レジストリ ファイル handsafe.reg を用意されています。 セーフ モードで実行するには、handsafe.reg を実行します。  
  
 Handsafe.reg を実行した後に、停止して、コマンド プロンプト ウィンドウで、次のコマンドを入力して、Web サーバー上の World Wide Web 発行サービスを再起動する必要があります:"NET 停止 W3SVC"および"NET 開始 W3SVC"です。  
  
## <a name="see-also"></a>参照  
 [DataFactory のカスタマイズ](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [RDS の基礎](../../../ado/guide/remote-data-service/rds-fundamentals.md)



