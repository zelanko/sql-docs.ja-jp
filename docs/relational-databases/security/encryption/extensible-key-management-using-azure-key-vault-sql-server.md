---
title: "Azure Key Vault を使用する拡張キー管理 (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Key Vault による拡張キー管理"
  - "Transparent Data Encryption、EKM および Key Vault を使用"
  - "EKM、Key Vault を使用"
  - "TDE、EKM および Key Vault"
  - "Key Vault によるキーの管理"
  - "SQL Server コネクタ, 概要"
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
caps.latest.revision: 66
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 66
---
# Azure Key Vault を使用する拡張キー管理 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 用の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタを使用すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の暗号化において、Azure Key Vault サービスを[拡張キー管理 &#40;EKM&#41;](../../../relational-databases/security/encryption/extensible-key-management-ekm.md) プロバイダーに使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の暗号化キーを保護することができます。  
  
 このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタについて説明します。 その他の情報については、「[Azure Key Vault を使用した拡張キー管理のセットアップ手順](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md)」、「[SQL 暗号化機能への SQL Server コネクタの使用](../../../relational-databases/security/encryption/use-sql-server-connector-with-sql-encryption-features.md)」、「[SQL Server コネクタのメンテナンスとトラブルシューティング](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md)」を参照してください。  
  
##  <a name="Uses"></a> 拡張キー管理 (EKM) の概要と用途  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、[Transparent Data Encryption &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption-tde.md)、[列レベルの暗号化](../../../t-sql/functions/cryptographic-functions-transact-sql.md) (CLE)、[バックアップの暗号化](../../../relational-databases/backup-restore/backup-encryption.md)など、機密データの保護に有効ないくつかの種類の暗号化が用意されています。 いずれのケースも、この従来のキー階層では、対称データ暗号化キー (DEK) を使用してデータが暗号化されます。 対称なデータ暗号化キーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に格納されたキーの階層で暗号化することにより、さらに保護されます。 このモデルに代わるのが、EKM プロバイダー モデルです。 EKM プロバイダーのアーキテクチャでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の外側にある外部暗号化サービス プロバイダーに格納された非対称キーを使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でデータの暗号化キーを保護することができます。 このモデルによって、セキュリティの層が拡充され、キーとデータの管理が分離されます。  
   
 次の図は、従来のサービスにおけるキー管理階層と Azure Key Vault システムとを比較したものです。  
  
 ![ekm-key-hierarchy-traditional](../../../relational-databases/security/encryption/media/ekm-key-hierarchy-traditional.png "ekm-key-hierarchy-traditional")  
  
   
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタが、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と Azure Key Vault の橋渡し的役割を担うことで、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、Azure Key Vault サービスのスケーラビリティ、高パフォーマンス、高可用性を活かすことができます。 以下の図は、EKM プロバイダー アーキテクチャにおけるキーの階層が、Azure Key Vault および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コネクタと連動するようすを表しています。  
  
  Azure Key Vault は、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Virtual Machines 上の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インストール環境で使用したり、オンプレミス サーバー用に使用したりすることが可能です。 また、資格情報コンテナー サービスでは、厳密な管理および監視下にあるハードウェア セキュリティ モジュール (HSM) を使用し、非対称暗号化キーをより高いレベルで保護するオプションも提供します。 資格情報コンテナーの詳細については、「[Azure Key Vault](http://go.microsoft.com/fwlink/?LinkId=521401)」を参照してください。  
  
 次の図は、Key Vault を使用した EKM のプロセス フローについてまとためものです。 (図の中にプロセス手順番号が示されていますが、図の後に示す設定手順の番号と対応しているわけではありません。)  
  
 ![SQL Server EKM using the Azure Key Vault](../../../relational-databases/security/encryption/media/ekm-using-azure-key-vault.png "SQL Server EKM using the Azure Key Vault")  

> [!NOTE]  
>  1.0.0.440 以前のバージョンは置き換えられ、実稼働環境ではサポートされなくなりました。 [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=45344)にアクセスし、[[SQL Server コネクタのメンテナンスとトラブルシューティング]](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md) ページの "SQL Server コネクタのアップグレード" に示されている手順を使用して、バージョン 1.0.1.0 以降にアップグレードしてください。
  
 次の手順については、「[Azure Key Vault を使用した拡張キー管理のセットアップ手順](../../../relational-databases/security/encryption/setup-steps-for-extensible-key-management-using-the-azure-key-vault.md)」を参照してください。  
  
 使用シナリオについては、「[SQL 暗号化機能への SQL Server コネクタの使用](../../../relational-databases/security/encryption/use-sql-server-connector-with-sql-encryption-features.md)」を参照してください。  
  
## 参照  
 [SQL Server コネクタのメンテナンスとトラブルシューティング](../../../relational-databases/security/encryption/sql-server-connector-maintenance-troubleshooting.md)  
  
  