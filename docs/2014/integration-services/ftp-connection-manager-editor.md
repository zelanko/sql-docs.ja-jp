---
title: FTP 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP Connection Manager Editor
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f5aebb659db6eabd79c6e707b8b47abf21909a88
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425339"
---
# <a name="ftp-connection-manager-editor"></a>FTP 接続マネージャー エディター
  **[FTP 接続マネージャー エディター]** ダイアログ ボックスを使用すると、FTP サーバーに接続するためのプロパティを指定できます。  
  
> [!IMPORTANT]  
>  FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
 FTP 接続マネージャーの詳細については、「 [FTP 接続マネージャー](connection-manager/ftp-connection-manager.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **サーバー名**  
 FTP サーバーの名前を指定します。  
  
 **サーバーポート**  
 接続に使用する FTP サーバーのポート番号を指定します。 このプロパティの既定値は **21**です。  
  
 **ユーザー名**  
 FTP サーバーにアクセスするために使用するユーザー名を指定します。 このプロパティの既定値は **anonymous**です。  
  
 **パスワード**  
 FTP サーバーにアクセスするために使用するパスワードを指定します。  
  
 **[タイムアウト (秒)]**  
 タスクがタイムアウトするまでの秒数を指定します。値**0**は、時間が無制限であることを示します。 このプロパティの既定値は **60**です。  
  
 **[パッシブ モードを使用する]**  
 サーバーまたはクライアントのどちらが接続を開始するかを指定します。 アクティブ モードではサーバーが接続を開始し、パッシブ モードではクライアントが接続を開始します。 このプロパティの既定値は **アクティブ モード**です。  
  
 **再試行**  
 接続を試行する回数を指定します。 値 **0** は、無制限に再試行を行うことを示します。  
  
 **[チャンク サイズ (KB)]**  
 データを転送するためのチャンク サイズを KB 単位で指定します。  
  
 **接続をテスト**  
 FTP 接続マネージャーを構成した後に、 **[接続テスト]** をクリックして、接続が利用可能であることを確認します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
