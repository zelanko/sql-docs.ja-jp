---
title: FTP タスク エディター (全般 ページ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 786f0d4371773f77045f0ef9cd6825057c12a937
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165870"
---
# <a name="ftp-task-editor-general-page"></a>[FTP タスク エディター] ([全般] ページ)
  **[FTP タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、タスクの通信先の FTP サーバーに接続する FTP 接続マネージャーを指定できます。 また、FTP タスクの名前と説明を入力することもできます。  
  
 このタスクの詳細については、「 [FTP タスク](control-flow/ftp-task.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[FtpConnection]**  
 既存の FTP 接続マネージャーを選択するか、[\<**新しい接続...**>] をクリックして接続マネージャーを作成します。  
  
> [!IMPORTANT]  
>  FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。 Windows 認証はサポートされていません。  
  
 **関連トピック**: [FTP 接続マネージャー](connection-manager/ftp-connection-manager.md)、 [FTP 接続マネージャー エディター](../../2014/integration-services/ftp-connection-manager-editor.md)  
  
 **[StopOnFailure]**  
 FTP 操作が失敗した場合に FTP タスクを終了するかどうかを示します。  
  
 **Name**  
 FTP タスクの一意な名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **description**  
 FTP タスクの説明を入力します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [FTP タスク エディター&#40;ファイル転送 ページ&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  