---
title: "FTP 接続マネージャー エディター | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ftpconnectionmanager.f1"
helpviewer_keywords: 
  - "FTP 接続マネージャー エディター"
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# FTP 接続マネージャー エディター
  **[FTP 接続マネージャー エディター]** ダイアログ ボックスを使用すると、FTP サーバーに接続するためのプロパティを指定できます。  
  
> [!IMPORTANT]  
>  FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
 FTP 接続マネージャーの詳細については、「[FTP 接続マネージャー](../../integration-services/connection-manager/ftp-connection-manager.md)」を参照してください。  
  
## オプション  
 **サーバー名**  
 FTP サーバーの名前を指定します。  
  
 **[サーバー ポート]**  
 接続に使用する FTP サーバーのポート番号を指定します。 このプロパティの既定値は **21**です。  
  
 **ユーザー名**  
 FTP サーバーにアクセスするために使用するユーザー名を指定します。 このプロパティの既定値は **anonymous** です。  
  
 **Password**  
 FTP サーバーにアクセスするために使用するパスワードを指定します。  
  
 **[タイムアウト (秒)]**  
 タスクがタイムアウトするまでの秒数を指定します。 この値に **0** を指定すると、時間は無制限になります。 このプロパティの既定値は **60**です。  
  
 **[パッシブ モードを使用する]**  
 サーバーまたはクライアントのどちらが接続を開始するかを指定します。 アクティブ モードではサーバーが接続を開始し、パッシブ モードではクライアントが接続を開始します。 このプロパティの既定値は**アクティブ モード**です。  
  
 **[再試行の回数]**  
 接続を試行する回数を指定します。 値 **0** は、無制限に再試行を行うことを示します。  
  
 **[チャンク サイズ (KB)]**  
 データを転送するためのチャンク サイズを KB 単位で指定します。  
  
 **[接続テスト]**  
 FTP 接続マネージャーを構成した後に、**[接続テスト]** をクリックして、接続が利用可能であることを確認します。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)  
  
  