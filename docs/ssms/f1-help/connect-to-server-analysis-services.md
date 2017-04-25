---
title: "[サーバーへの接続] (Analysis Services) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connection.login.analysisserver.f1
ms.assetid: 7e277d22-8d4b-422e-8882-7c5dd7a6d915
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 73451189bc401a4167c65261f3adcc5aabb6627c
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-analysis-services"></a>[サーバーへの接続] (Analysis Services)
このダイアログを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] に接続するときのオプションを表示または指定できます。  
  
## <a name="options"></a>オプション  
**サーバーの種類**  
オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../../includes/ssde_md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。 ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。 [登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。 別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../../includes/ssde_md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。  
  
**サーバー名**  
接続するサーバー インスタンスを選択します。 既定では、最後に接続していたサーバー インスタンスが表示されます。  
  
**[認証]**  
Analysis Services のインスタンスに接続するときは、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 認証モードがサポートされます。  
  
**Windows 認証モード ([Windows 認証])**  
**Windows 認証** モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。  
  
**ユーザー名**  
このオプションは、このリリースでは使用できません。 接続に使用するユーザー名を入力します。 このオプションは、 **Windows 認証**を使用した接続を選択した場合のみ使用できます。  
  
**Password**  
このオプションは、このリリースでは使用できません。 ログインのパスワードを入力します。 このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 認証を使用した接続を選択した場合のみ編集できます。  
  
**Connect**  
クリックすると、上記で選択したサーバーに接続します。  
  
**オプション**  
クリックすると、サーバーの登録やパスワードの保存など、追加のサーバー接続オプションが表示されます。  
  

