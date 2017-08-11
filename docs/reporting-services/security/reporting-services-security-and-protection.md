---
title: "Reporting Services のセキュリティと保護 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
caps.latest.revision: 21
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 217bd93631e96dae0b75532d73c14ade4355be6d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="reporting-services-security-and-protection"></a>Reporting Services のセキュリティと保護
  このセクションの情報を使用するには、セキュリティ機能について学習する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]です。 また、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]でサポートされている承認モデルと認証プロバイダーについても説明します。  
  
## <a name="extended-protection-for-authentication"></a>認証の拡張保護 (Extended Protection for Authentication)  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]以降では、認証の拡張保護がサポートされています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能により、認証の拡張保護に対するチャネル バインドとサービス バインドの使用がサポートされます。 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能は、拡張保護がサポートされているオペレーティング システムで使用する必要があります。 詳細については、「 [Reporting Services での認証の拡張保護](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)」をご覧ください。  
  
## <a name="authentication-and-authorization"></a>認証と承認  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ユーザーと、レポート サーバーでの認証にクライアント アプリケーションの種類の認証を提供します。 レポート サーバーの適切な認証の種類を使用すると、組織で必要とされる適切なレベルのセキュリティを実現できます。 詳細については、「 [レポート サーバーでの認証](../../reporting-services/security/authentication-with-the-report-server.md)」を参照してください。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ロールとユーザー (つまり、何にアクセスできることができ、どのように法人アクセスできる) は、レポート サーバーのカタログ内のコンテンツへのアクセスを制御するアクセス許可を使用します。 詳細については、「[ロールと権限 &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md)」を参照してください。  
  
## <a name="related-tasks"></a>関連タスク  
  
|タスクの説明|リンク|  
|-----------------------|-----------|  
|レポート サーバーへのクライアント接続を保護するための Secure Socket Layer (SSL) の構成|[ネイティブ モード レポート サーバーで SSL 接続を構成します。](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  

