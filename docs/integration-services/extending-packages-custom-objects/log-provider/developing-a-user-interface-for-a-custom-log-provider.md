---
title: カスタム ログ プロバイダー用ユーザー インターフェイスの開発 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fccc03acb846fe1fe7db12d339c633b7d4c7e306
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "71297137"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a>カスタム ログ プロバイダー用ユーザー インターフェイスの開発

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  多くの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ログ プロバイダーには、カスタム ユーザー インターフェイスがあります。カスタム ユーザー インターフェイスには <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> が実装され、**[SSIS ログの構成]** ダイアログ ボックスの **[構成]** ボックスが、使用可能な接続マネージャーがフィルター選択されたドロップダウン リストに置き換えられます。 ただし、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では実装されていません。  
  
## <a name="see-also"></a>参照  
 [カスタム ログ プロバイダーの作成](../../../integration-services/extending-packages-custom-objects/log-provider/creating-a-custom-log-provider.md)   
 [カスタム ログ プロバイダーのコーディング](../../../integration-services/extending-packages-custom-objects/log-provider/coding-a-custom-log-provider.md)  
  
  
