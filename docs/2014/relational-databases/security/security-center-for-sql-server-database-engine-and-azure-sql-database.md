---
title: SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- SQL Server, security
- security [SQL Server]
- database security [SQL Server]
- databases [SQL Server], security
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 131fb3639f84c1b59796d59bcfff17159da8f063
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028660"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>SQL Server データベース エンジンと Azure SQL Database のセキュリティ センター
  このページでは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]および [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]でのセキュリティと保護に関して必要になる情報の検索に役立つリンクを示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] の機能は向上し続けます。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]に関する最新情報については、このトピックの最新バージョンをご覧ください。  
  
|認証:ユーザーはだれか|権限何を実行できるか|よる秘密データの格納|接続のセキュリティ:制限と保護|監査: アクセスの記録|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**だれが認証したか**<br /><br /> [![Security Center マップの Windows 認証](../../database-engine/media/security-center-map-windows-authenticaion.png "Security Center マップの Windows 認証")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Security Center マップ SQL Server 認証](../../database-engine/media/security-center-map-sql-authenticaion.png "Security Center マップ SQL Server 認証")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **どこで認証されたか**<br /><br /> [![ログインとユーザーをマップ Security Center](../../database-engine/media/security-center-map-logins-users.png "にはログインとユーザーをマップ Security Center")には](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![包含データベースユーザーをマップ Security Center](../../database-engine/media/security-center-map-contained-users.png "には包含データベースユーザーをマップ Security Center")](https://msdn.microsoft.com/library/ff929188.aspx)には<br /><br /> **他の ID の使用**<br /><br /> [![資格情報のマップ Security Center](../../database-engine/media/security-center-map-credentials.png "資格情報のマップ Security Center")](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Security Center をログインとしてマップ](../../database-engine/media/security-center-map-exec-as-login.png "するSecurity Center をログインとしてマップ")](https://msdn.microsoft.com/library/ms181362.aspx)する<br /><br /> [![Security Center をユーザーとしてマップ](../../database-engine/media/security-center-map-exec-as-user.png "するSecurity Center をユーザーとしてマップ")する](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")|**権限の許可、取り消し、および拒否**<br /><br /> [![セキュリティ保護可能なクラスをマップ Security Center](../../database-engine/media/security-center-map-securable-classes.png "にはセキュリティ保護可能なクラスをマップ Security Center")には](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Security Center マップサーバーのアクセス許可](../../database-engine/media/security-center-map-srv-perms.png "Security Center マップサーバーのアクセス許可")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Security Center マップデータベースの権限](../../database-engine/media/security-center-map-db-perms.png "Security Center マップデータベースの権限")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **ロールによるセキュリティ**<br /><br /> [![Security Center マップサーバーロール](../../database-engine/media/security-center-map-srv-roles.png "Security Center マップサーバーロール")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Security Center マップデータベースロール](../../database-engine/media/security-center-map-db-roles.png "Security Center マップデータベースロール")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Security Center マップのビューとプロシージャ](../../database-engine/media/security-center-map-view-procs.png "Security Center マップのビューとプロシージャ")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Security Center マップ行レベルセキュリティ](../../database-engine/media/security-center-map-row-level-sec.png "Security Center マップ行レベルセキュリティ")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Security Center マップ動的データマスク](../../database-engine/media/security-center-map-data-masking.png "Security Center マップ動的データマスク")](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [署名された![オブジェクトを Security Center マップ](../../database-engine/media/security-center-map-signed-objects.png "するには署名されたオブジェクトを Security Center マップ")するには](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")|**ファイルの暗号化**<br /><br /> [![Security Center マップの BitLocker](../../database-engine/media/security-center-map-bitlocker.png "Security Center マップの BitLocker")](https://support.microsoft.com/en-us/kb/2855131)<br /><br /> [![NTFS 暗号化の Security Center マップ](../../database-engine/media/security-center-map-ntfs-encryp.png "NTFS 暗号化の Security Center マップ")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![マップ TDE の Security Center](../../database-engine/media/security-center-map-tde.png "マップ TDE の Security Center")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Security Center マップのバックアップ暗号化](../../database-engine/media/security-center-map-backup-encryp.png "Security Center マップのバックアップ暗号化")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **ソースの暗号化**<br /><br /> [![Security Center マップ EKM](../../database-engine/media/security-center-map-ekm.png "Security Center マップ EKM")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Security Center マップ Azure Key Vault](../../database-engine/media/security-center-map-key-vault.png "Security Center マップ Azure Key Vault")](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **列、データ & キーの暗号化**<br /><br /> [![証明書による暗号化をマップ Security Center](../../database-engine/media/security-center-map-cert.png "証明書による暗号化をマップ Security Center")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![対称キーによる暗号化をマップ Security Center](../../database-engine/media/security-center-map-sym-key.png "対称キーによる暗号化をマップ Security Center")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![非対称キーによる暗号化をマップ Security Center](../../database-engine/media/security-center-map-asym-key.png "非対称キーによる暗号化をマップ Security Center")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![パスフレーズによる暗号化をマップ Security Center](../../database-engine/media/security-center-map-passphrase.png "パスフレーズによる暗号化をマップ Security Center")](https://msdn.microsoft.com/library/ms190357.aspx)|**ファイアウォールによる防御**<br /><br /> [![Security Center マップの Windows ファイアウォール](../../database-engine/media/security-center-map-windows-firewall.png "Security Center マップの Windows ファイアウォール")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Security Center マップサービスのファイアウォール](../../database-engine/media/security-center-map-service-firewall.png "Security Center マップサービスのファイアウォール")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Security Center マップデータベースファイアウォール](../../database-engine/media/security-center-map-db-firewall.png "Security Center マップデータベースファイアウォール")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **転送中のデータの暗号化**<br /><br /> [![Security Center マップの強制 SSL](../../database-engine/media/security-center-map-forced-ssl.png "Security Center マップの強制 SSL")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![オプションの SSL をマップ Security Centerには](../../database-engine/media/security-center-map-opt-ssl.png "オプションの SSL をマップ Security Centerには")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")|**自動監査**<br /><br /> [![Security Center マップ SQL Server 監査](../../database-engine/media/security-center-map-sql-audit.png "Security Center マップ SQL Server 監査")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Security Center マップ SQL Database 監査](../../database-engine/media/security-center-map-sqldb-audit.png "Security Center マップ SQL Database 監査")](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **カスタム監査**<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> [![Security Center マップトリガー](../../database-engine/media/security-center-map-triggers.png "Security Center マップトリガー")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **準拠**<br /><br /> [![Secctrcompliance](../../database-engine/media/secctrcompliance.png "Secctrcompliance")](https://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![プレースホルダー](../../database-engine/media/security-center-map-blankplaceholder.png "プレースホルダー")<br /><br /> ![Security Center の凡例](../../database-engine/media/security-center-map-legend.png "Security Center の凡例")|  
  
## <a name="links-to-specific-related-topics"></a>関連する特定のトピックへのリンク  
 ![小さいファイルフォルダーアイコン](../../integration-services/media/filefolder-small.gif "小さいファイルフォルダーアイコン")**認証:あなたは誰ですか。**  
 **だれが認証するか(Windows また[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は)**  
  
-   [認証モードの選択](choose-an-authentication-mode.md)  
  
 **master データベースでの認証** (ログインとデータベース ユーザー)  
  
-   [SQL Server ログインの作成](authentication-access/create-a-login.md)  
  
-   [Azure SQL データベースにおけるデータベースとログインの管理](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [データベース ユーザーの作成](authentication-access/create-a-database-user.md)  
  
 **ユーザーデータベースでの認証**  
  
-   [包含データベース ユーザー - データベースの可搬性を確保する](contained-database-users-making-your-database-portable.md)  
  
 **他の ID の使用**  
  
-   [資格情報 &#40;データベース エンジン&#41;](authentication-access/credentials-database-engine.md)  
  
-   [別のログインとして実行](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [別のデータベース ユーザーとして実行](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![小さいファイルフォルダーアイコン](../../integration-services/media/filefolder-small.gif "小さいファイルフォルダーアイコン")**暗号化:シークレットデータの格納**  
 **ファイルの暗号化**  
  
-   [BitLocker (ドライブ レベル)](https://support.microsoft.com/kb/2855131)  
  
-   [NTFS 暗号化 (フォルダー レベル)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [透過的なデータ暗号化 (ファイル レベル)](encryption/transparent-data-encryption.md)  
  
-   [バックアップの暗号化 (ファイル レベル)](../backup-restore/backup-encryption.md)  
  
 **ソースの暗号化**  
  
-   [拡張キー管理モジュール](encryption/extensible-key-management-ekm.md)  
  
-   [Azure キー コンテナーに格納されたキー](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **列、データ、キーの暗号化**  
  
-   [証明書による暗号化](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [非対称キーによる暗号化](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [対称キーによる暗号化](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [パスフレーズによる暗号化](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![小さいファイルフォルダーアイコン](../../integration-services/media/filefolder-small.gif "小さいファイルフォルダーアイコン")**承認:どうすればよいですか。**  
 **権限の許可、取り消し、および拒否**  
  
-   [権限の階層 &#40;データベース エンジン&#41;](permissions-hierarchy-database-engine.md)  
  
-   [権限](permissions-database-engine.md)  
  
-   [セキュリティ保護可能](securables.md)  
  
 **ロールによるセキュリティ**  
  
-   [サーバー レベルのロール](authentication-access/server-level-roles.md)  
  
-   [データベース レベルのロール](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   [ビュー](../views/views.md) と [プロシージャ](../stored-procedures/stored-procedures-database-engine.md)を使用したデータ アクセスの制限  
  
-   [行レベルのセキュリティ](https://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [動的なデータ マスキング](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [署名済みオブジェクト](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![小さいファイルフォルダーアイコン](../../integration-services/media/filefolder-small.gif "小さいファイルフォルダーアイコン")**接続のセキュリティ:制限とセキュリティ保護**  
 **ファイアウォールによる防御**  
  
-   [データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Azure SQL データベースのファイアウォール設定](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Azure サービスのファイアウォール設定](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **転送中のデータの暗号化**  
  
-   [データベース エンジンの Secure Sockets Layer](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [SQL データベースの Secure Sockets Layer](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![小さいファイルフォルダーアイコン](../../integration-services/media/filefolder-small.gif "小さいファイルフォルダーアイコン")**監査:アクセスの記録**  
 **自動監査**  
  
-   [SQL Server Audit &#40;データベース エンジン&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [SQL データベースの監査](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **カスタム監査の実装**  
  
-   [DDL Triggers](../triggers/ddl-triggers.md) と [DML Triggers](../triggers/dml-triggers.md)の作成  
  
 ![小さいファイルフォルダーアイコン](../../integration-services/media/filefolder-small.gif "小さいファイルフォルダーアイコン")**コンプライアンス**  
 **SQL Server**  
  
-   [情報セキュリティ国際評価基準](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **SQL Database**  
  
-   [Microsoft Azure セキュリティ センター:機能ごとのコンプライアンス](https://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>関連項目  
 [SQL Server の保護](securing-sql-server.md)   
 [プリンシパル &#40;データベース エンジン&#41;](authentication-access/principals-database-engine.md)   
 [SQL Server の証明書と非対称キー](sql-server-certificates-and-asymmetric-keys.md)   
 [SQL Server の暗号化](encryption/sql-server-encryption.md)   
 [セキュリティ構成](surface-area-configuration.md)   
 [強力なパスワード](strong-passwords.md)   
 [TRUSTWORTHY データベース プロパティ](trustworthy-database-property.md)   
 [データベース エンジンの機能とタスク](../../database-engine/database-engine-features-and-tasks.md)  
  
  
