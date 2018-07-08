---
title: セキュリティの概要 (レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- authorization [SQL Server replication]
- cryptography [SQL Server replication]
- encryption [SQL Server replication]
- security [SQL Server replication], about security
- authentication [SQL Server replication]
ms.assetid: 27828fe4-3b54-4c33-886e-08e8279e34b5
caps.latest.revision: 44
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 62567dbbb53db61780f002779abb825e19287578
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148263"
---
# <a name="security-overview-replication"></a>セキュリティの概要 (レプリケーション)
  レプリケーション環境をセキュリティで保護するには、基本的には、認証と承認のオプション、レプリケーション フィルター機能の適切な使用方法、およびレプリケーション環境の各要素をセキュリティで保護するための個々の手法を把握する必要があります。 レプリケーション環境には、ディストリビューター、パブリッシャー、サブスクライバー、スナップショット フォルダーなどが含まれます。 ここでは、レプリケーションのセキュリティについて説明しますが、レプリケーションのセキュリティは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セキュリティや Windows セキュリティをベースにしています。 したがって、この基盤とレプリケーションのセキュリティの詳細を理解する必要があります。 セキュリティの詳細については、「[SQL Server インストールにおけるセキュリティの考慮事項](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md)」を参照してください。 Oracle パブリッシングのセキュリティの注意点に関する詳細については、「 [Design Considerations and Limitations for Oracle Publishers](../non-sql/design-considerations-and-limitations-for-oracle-publishers.md)」の「レプリケーションのセキュリティ モデル」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [脅威と脆弱性の対策 &#40;レプリケーション&#41;](threat-and-vulnerability-mitigation-replication.md)  
 レプリケーション トポロジに対する潜在的な脅威と、それらの脅威を軽減する方法について説明します。  
  
 [ID およびアクセス制御 &#40;レプリケーション&#41;](identity-and-access-control-replication.md)  
 認証、承認、およびフィルター選択を使用してレプリケーション トポロジをセキュリティで保護する方法について説明します。  
  
 [セキュリティで保護された開発 &#40;レプリケーション&#41;](secure-development-replication.md)  
 レプリケーションのセキュリティの動作、レプリケーションのセキュリティの推奨事項、およびレプリケーションの最小権限について説明します。  
  
 [セキュリティで保護された配置 &#40;レプリケーション&#41;](secure-deployment-replication.md)  
 レプリケーション トポロジのすべてのコンポーネントに対するセキュリティを強化する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [セキュリティと保護 (レプリケーション)](security-and-protection-replication.md)  
  
  
