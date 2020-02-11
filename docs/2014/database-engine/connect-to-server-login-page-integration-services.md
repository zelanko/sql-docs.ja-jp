---
title: '[サーバーへの接続]([ログイン] ページ) (Integration Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53a9793fc2a8770c8d926c945ba31a335bdfed3f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62808733"
---
# <a name="connect-to-server-login-page-integration-services"></a>[サーバーへの接続] ([ログイン] ページ) (Integration Services)
  このタブを使用すると、に[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]接続するときに、次のオプションを表示または指定できます。  
  
## <a name="options"></a>オプション  
 **サーバーの種類**  
 オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。 ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。 [登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。 別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。  
  
 **サーバー名**  
 接続するサーバーを選択します。 既定では、最後に接続していたサーバー インスタンスが表示されます。  
  
> [!NOTE]  
>  はコンピューター上の複数のインスタンスをサポート[!INCLUDE[ssIS](../includes/ssis-md.md)]していないため、 * \<servername>* \\ * \<instancename>* を使用しないでください。  
  
 **認証**  
 
  [!INCLUDE[msCoName](../includes/msconame-md.md)] では [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows 認証だけを使用できます。 Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。  
  
 **ユーザー名**  
 
  [!INCLUDE[ssIS](../includes/ssis-md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。  
  
 **パスワード**  
 
  [!INCLUDE[ssIS](../includes/ssis-md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。  
  
 **パスワードを保存する**  
 
  [!INCLUDE[ssIS](../includes/ssis-md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。  
  
 **接続する**  
 上で選択したサーバーに接続します。  
  
 **オプション**  
 クリックすると、ダイアログが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。  
  
  
