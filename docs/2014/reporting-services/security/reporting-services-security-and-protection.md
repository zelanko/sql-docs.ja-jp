---
title: Reporting Services のセキュリティと保護 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
caps.latest.revision: 20
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3be671426856e57e62ea7de3733f6109bbcd0a31
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232452"
---
# <a name="reporting-services-security-and-protection"></a>Reporting Services のセキュリティと保護
  このセクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のセキュリティ機能について説明します。 また、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]でサポートされている承認モデルと認証プロバイダーについても説明します。  
  
## <a name="extended-protection-for-authentication"></a>認証の拡張保護 (Extended Protection for Authentication)  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]以降では、認証の拡張保護がサポートされています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能により、認証の拡張保護に対するチャネル バインドとサービス バインドの使用がサポートされます。 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能は、拡張保護がサポートされているオペレーティング システムで使用する必要があります。 詳細については、次を参照してください。 [Authentication with Reporting Services の拡張保護](extended-protection-for-authentication-with-reporting-services.md)します。  
  
## <a name="authentication-and-authorization"></a>認証と承認  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート サーバーで認証を行うためのさまざまな認証の種類が、ユーザーおよびクライアント アプリケーションに提供されます。 レポート サーバーの適切な認証の種類を使用すると、組織で必要とされる適切なレベルのセキュリティを実現できます。 詳細については、「 [レポート サーバーでの認証](authentication-with-the-report-server.md)」を参照してください。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート サーバー カタログ内のコンテンツへのユーザー アクセス (つまり、アクセスできるユーザーとそのユーザーがアクセスできるコンテンツ、およびアクセス方法) を制御するためのロールと権限も使用されます。 詳細については、「[ロールと権限 (Reporting Services)](roles-and-permissions-reporting-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|タスクの説明|リンク|  
|-----------------------|-----------|  
|レポート サーバーへのクライアント接続を保護するための Secure Socket Layer (SSL) の構成|[ネイティブ モードのレポート サーバーでの SSL 接続の構成](configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
