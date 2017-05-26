---
title: "[サーバーへの接続] ([ログイン] ページ) (Integration Services) | Microsoft Docs"
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
- sql13.swb.connecttodts.login.f1
- sql13.swb.connecttodtsserver.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 18699131b8268dedfb0e47f05ec4032d81b498ef
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-login-page-integration-services"></a>[サーバーへの接続] \([ログイン] ページ) (Integration Services)
このタブは、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)] に接続するときに以下のオプションを表示または指定する場合に使用します。  
  
## <a name="options"></a>オプション  
**サーバーの種類**  
オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../../includes/ssde_md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。 ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。 [登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。 別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../../includes/ssde_md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。  
  
**サーバー名**  
接続するサーバーを選択します。 既定では、最後に接続していたサーバー インスタンスが表示されます。  
  
> [!NOTE]  
> *<servername>*\\*<instancename>*を使用しないでください。 [!INCLUDE[ssIS](../../includes/ssis_md.md)] では、1 台のコンピューター上で複数のインスタンスはサポートされません。  
  
**[認証]**  
[!INCLUDE[msCoName](../../includes/msconame_md.md)] では [!INCLUDE[ssIS](../../includes/ssis_md.md)]Windows 認証だけを使用できます。 Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。  
  
**ユーザー名**  
[!INCLUDE[ssIS](../../includes/ssis_md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。  
  
**Password**  
[!INCLUDE[ssIS](../../includes/ssis_md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。  
  
**[パスワードを保存する]**  
[!INCLUDE[ssIS](../../includes/ssis_md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。  
  
**Connect**  
上で選択したサーバーに接続します。  
  
**オプション**  
クリックすると、ダイアログが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。  
  

