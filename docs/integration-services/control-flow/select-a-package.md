---
title: '[パッケージの選択] | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1045623c5eabe80a66a9320cb8425b47788d950d
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921148"
---
# <a name="select-a-package"></a>[パッケージの選択]

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  **[パッケージの選択]** ダイアログ ボックスを使用すると、メッセージ キュー タスクで受信されるメッセージの送信元パッケージを指定できます。  
  
## <a name="static-options"></a>静的オプション  
 **Location**  
 パッケージの場所を特定します。 このプロパティのオプションを次の表に示します。  
  
|値|説明|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|場所を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに設定します。 この値を選択すると、動的オプションの [パッケージ名]、 **[サーバー]** 、 **[Windows 認証を使用する]** 、 **[SQL Server 認証を使用する]** 、 **[ユーザー名]** 、および **[パスワード]** が表示されます。|  
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
  
 **ユーザー名**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、サーバーにログオンするときに使用するユーザー名を入力します。  
  
 **パスワード**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、パスワードを指定します。  
  
### <a name="location--dtsx-file"></a>[場所] = [DTSX ファイル]  
 **[ファイル名]**  
 パッケージのパスを入力するか、参照ボタン ( **[...]** ) をクリックしてパッケージを指定します。  
  
## <a name="see-also"></a>参照  
 [メッセージ キュー タスク](../../integration-services/control-flow/message-queue-task.md)  
  
  
