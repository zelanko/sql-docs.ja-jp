---
title: '[パッケージの選択] | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f19490ea376b4a0aa8ecae8fdaae251376a56b3c
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334776"
---
# <a name="select-a-package"></a>[パッケージの選択]
  **[パッケージの選択]** ダイアログ ボックスを使用すると、メッセージ キュー タスクで受信されるメッセージの送信元パッケージを指定できます。  
  
## <a name="static-options"></a>静的オプション  
 **場所**  
 パッケージの場所を特定します。 このプロパティのオプションを次の表に示します。  
  
|ReplTest1|[説明]|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|場所を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに設定します。 この値を選択すると、動的オプションの [パッケージ名]、 **[サーバー]**、 **[Windows 認証を使用する]**、 **[SQL Server 認証を使用する]**、 **[ユーザー名]**、および **[パスワード]** が表示されます。|  
|[DTSX ファイル]|DTSX ファイルの場所を設定します。 この値を選択すると、動的オプションの **[ファイル名]** が表示されます。|  
  
## <a name="location-dynamic-options"></a>[Location] の動的オプション  
  
### <a name="location--sql-server"></a>Location = SQL Server  
 **パッケージ名**  
 指定したサーバーに格納されているパッケージを選択します。  
  
 **[サーバー]**  
 サーバーの名前を入力するか、サーバーを一覧から選択します。  
  
 **[Windows 認証を使用する]**  
 Windows 認証を使用する場合にクリックします。  
  
 **[SQL Server 認証を使用する]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合にクリックします。  
  
 **User name**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、サーバーにログオンするときに使用するユーザー名を入力します。  
  
 **Password**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、パスワードを入力します。  
  
### <a name="location--dtsx-file"></a>[場所] = [DTSX ファイル]  
 **[ファイル名]**  
 パッケージのパスを入力するか、参照ボタン ( **[...]** ) をクリックしてパッケージを指定します。  
  
## <a name="see-also"></a>参照  
 [メッセージ キュー タスク](../../integration-services/control-flow/message-queue-task.md)  
  
  
