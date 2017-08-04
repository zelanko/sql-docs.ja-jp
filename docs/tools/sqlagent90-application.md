---
title: "sqlagent90 アプリケーション |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- starting SQL Server Agent
- sqlagent90 application
- SQL Server Agent, starting
- command prompt utilities [SQL Server], sqlagent90
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9aa0fab5e21ffb7ac7b39728ed025a4b467f8102
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="sqlagent90-application"></a>sqlagent90 アプリケーション
  **sqlagent90** アプリケーションは、コマンド プロンプトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを起動します。 通常、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントは [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] から実行するか、またはアプリケーションで SQL-SMO メソッドを使って実行します。 ただし、 **エージェントを診断する場合や、プライマリ サポート プロバイダーから指示された場合は、コマンド プロンプトから** sqlagent90 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## <a name="arguments"></a>引数  
 **-c**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントをコマンド プロンプトから実行し、Microsoft Windows サービス コントロール マネージャーの制御下にないことを指定します。 **-c** を使用する場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを、管理ツールのサービス アプリケーションまたは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーから制御することはできません。 この引数は必須です。  
  
 **-v**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを冗長モードで実行し、診断情報をコマンド プロンプト ウィンドウに書き込みます。 診断情報は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントのエラー ログに書き込まれる情報と同じです。  
  
 **-i** *instance_name*  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance_name *によって指定された名前付き*インスタンスに接続します。  
  
## <a name="remarks"></a>解説  
 **sqlagent90** は、 **-v** スイッチが指定された場合にのみ、著作権に関するメッセージを表示した後にコマンド プロンプト ウィンドウに出力を表示します。 **sqlagent90**を停止するには、コマンド プロンプトで Ctrl キーを押しながら C キーを押します。 **sqlagent90**を停止する前に、コマンド プロンプト ウィンドウを閉じないでください。  
  
## <a name="see-also"></a>参照  
 [管理タスクの自動化 &#40;SQL Server エージェント&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
