---
title: ユーザーのアクセス許可のテスト (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: 83a03b85-ea7f-4b4a-b19b-f7eca534ffae
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8ddcd6d754ce1b760d91462847b796e4ec8de933
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47594610"
---
# <a name="test-a-user39s-permissions-master-data-services"></a>ユーザーのアクセス許可のテスト (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、テスト ユーザーを作成し、Web アプリケーションにログインして権限をテストできます。ユーザーが [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] の URL にアクセスを試みると、ユーザーの資格情報が認証されます。 Internet Explorer のセキュリティ設定によって、自動認証を行うかユーザー名とパスワードの入力を求めるかが制御されます。 これらの設定を変更するには、次の手順を実行します。  
  
### <a name="to-test-a-users-security"></a>ユーザーのセキュリティをテストするには  
  
1.  Internet Explorer 7 以降で、 **[ツール]**、 **[インターネット オプション]** の順にクリックして、 **[セキュリティ]** タブをクリックします。  
  
2.  **[ローカル イントラネット]** をクリックして、 **[レベルのカスタマイズ]** ボタンをクリックします。  
  
3.  **[ユーザー認証]** セクションで **[ユーザー名とパスワードを入力してログオンする]** をクリックします。  
  
4.  次にブラウザー ウィンドウを開くときに、ユーザー名とパスワードの入力を求められます。  
  
## <a name="see-also"></a>参照  
 [セキュリティ (マスター データ サービス)](../master-data-services/security-master-data-services.md)  
  
  
