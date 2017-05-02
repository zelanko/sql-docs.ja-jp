---
title: MSSQLSERVER_18452 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7e08452accd39507cc3124ff4a1dc22a073c01dd
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver18452"></a>MSSQLSERVER_18452
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|18452|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LOGON_INVALID_CONNECT|  
|メッセージ テキスト|ユーザー '%.*ls' はログインできませんでした。 このログインは SQL Server ログインなので、Windows 認証では使用できません。%.\*ls|  
  
## <a name="explanation"></a>説明  
検証できない資格情報でユーザーがログインしようとしました。 次の原因が考えられます。  
  
-   ログインは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインですが、サーバーは Windows 認証のみを受け付けます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続しようとしていますが、使用しているログインが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に存在しません。  
  
-   ログインで Windows 認証を使用していますが、そのログインは認識できない Windows プリンシパルです。 認識できない Windows プリンシパルは、ログインを Windows で確認できないことを意味します。 これは、信頼されていないドメインからの Windows ログインである可能性があります。  
  
同様の問題によって、より広い意味のエラー 18456 が発生することがあります。  
  
## <a name="user-action"></a>ユーザーの操作  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続しようとしている場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が混合モード認証で構成されていることを確認します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用して接続しようとしている場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが存在することを確認します。  
  
Windows 認証を使用して接続しようとしている場合は、正しいドメインに適切にログインしていることを確認します。  
  

