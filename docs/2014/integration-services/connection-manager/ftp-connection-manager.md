---
title: FTP 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- FTP connection manager
- connections [Integration Services], FTP
- connection managers [Integration Services], FTP
ms.assetid: c4f43455-29ca-44ba-ac7f-ea729b1daf93
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 989049c5371d35d53282f5780dcfc9db13312c7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48188842"
---
# <a name="ftp-connection-manager"></a>FTP 接続マネージャー
  FTP 接続マネージャーを使用すると、パッケージは、ファイル転送プロトコル (FTP) サーバーに接続できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる FTP タスクでは、この接続マネージャーを使用します。  
  
 FTP 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は、実行時に FTP 接続として解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定し、接続マネージャーをパッケージの `Connections` コレクションに追加します。  
  
 `ConnectionManagerType`接続マネージャーのプロパティに設定されて`FTP`します。  
  
 FTP 接続マネージャーは、次の方法で構成できます。  
  
-   サーバー名とサーバー ポートを指定します。  
  
-   匿名アクセスを指定するか、または基本認証のユーザー名とパスワードを指定します。  
  
    > [!IMPORTANT]  
    >  FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
-   タイムアウト、再試行回数、および一度にコピーするデータ量を指定します。  
  
-   FTP 接続マネージャーでパッシブ モードを使用するか、アクティブ モードを使用するかを指定します。  
  
 FTP 接続マネージャーの接続先である FTP サイトの構成によっては、接続マネージャーの次の既定値の変更が必要になる場合があります。  
  
-   サーバー ポートは 21 に設定されています。 FTP サイトがリッスンするポートを指定する必要があります。  
  
-   ユーザー名は "anonymous" に設定されています。 FTP サイトで必要になる資格情報を指定する必要があります。  
  
## <a name="activepassive-modes"></a>アクティブ/パッシブ モード  
 FTP 接続マネージャーは、アクティブ モードまたはパッシブ モードのどちらかを使用して、ファイルを送受信できます。 アクティブ モードでは、サーバーがデータ接続を開始し、パッシブ モードでは、クライアントがデータ接続を開始します。  
  
## <a name="configuration-of-the-ftp-connection-manager"></a>FTP 接続マネージャーの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティについては、「 [[FTP 接続マネージャー エディター]](../ftp-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成方法の詳細については、次を参照してください。<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>と[プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)します。  
  
## <a name="see-also"></a>参照  
 [FTP タスク](../control-flow/ftp-task.md)   
 [Integration Services &#40;SSIS&#41;接続](integration-services-ssis-connections.md)  
  
  
