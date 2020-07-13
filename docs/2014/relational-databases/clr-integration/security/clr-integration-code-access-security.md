---
title: CLR 統合のコードアクセスセキュリティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
author: rothja
ms.author: jroth
ms.openlocfilehash: 75b283da2760b39349351802a83caae04e546c06
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953450"
---
# <a name="clr-integration-code-access-security"></a>CLR 統合のコード アクセス セキュリティ
  共通言語ランタイム (CLR) では、マネージド コードに対してコード アクセス セキュリティというセキュリティ モデルがサポートされます。 このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。 詳細については、.NET Framework Software Development Kit の「コード アクセス セキュリティ」を参照してください。  
  
 アセンブリに許可される権限を決定するセキュリティ ポリシーは、次の 3 つに分類されます。  
  
-   コンピューター ポリシー : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がインストールされているコンピューターで実行されるすべてのマネージド コードに対して効力を持つポリシーです。  
  
-   ユーザー ポリシー : 特定のプロセスをホストとするマネージド コードに対して効力を持つポリシーです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービスが実行されています。  
  
-   ホスト ポリシー : CLR のホスト (この場合は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) によって設定され、そのホストで実行されるマネージド コードに対して効力を持つポリシーです。  
  
 CLR でサポートされるコード アクセス セキュリティ メカニズムは、ランタイムが完全に信頼されるコードと部分的に信頼されるコードの両方をホストできるという前提に基づいています。 CLR コードアクセスセキュリティによって保護されているリソースは、通常、リソースへのアクセスを許可する前に、対応するアクセス許可を requirethe マネージアプリケーションプログラミングインターフェイスによってラップされます。 Demandfor は、呼び出し履歴のすべての呼び出し元 (アセンブリレベル) に対応するリソースアクセス許可がある場合にのみ、アクセス許可を満たしています。  
  
 内で実行するときにマネージコードに付与されるコードアクセスセキュリティのアクセス許可のセットは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込まれたアセンブリにアクセス許可のセットを付与し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。ユーザーコードに与えられる最終的なアクセス許可のセットは、ユーザーおよびコンピューターレベルのポリシーによってさらに制限される可能性があります。  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>SQL Server ホスト ポリシー レベルの権限セット  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシー レベルでアセンブリに許可されるコード アクセス セキュリティ権限のセットは、アセンブリの作成時にどの権限セットを指定するかによって決定されます。 権限セットには、、、およびの3つがあります。 `SAFE` `EXTERNAL_ACCESS` `UNSAFE` [CREATE ASSEMBLY &#40;transact-sql&#41;](/sql/t-sql/statements/create-assembly-transact-sql)) の**PERMISSION_SET**オプションを使用して指定します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. このポリシーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が CLR のインスタンスを作成するときに有効になる、既定のアプリケーション ドメイン用ではありません。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]システムアセンブリの fixedpolicy とユーザーアセンブリのユーザー指定ポリシー。  
  
 CLR アセンブリと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] システム アセンブリの固定ポリシーでは、これらのアセンブリを完全に信頼します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシーのユーザー指定部分は、アセンブリの所有者がアセンブリごとに指定する 3 つの権限バケットのいずれかに基づきます。 次に示すセキュリティ権限の詳細については、.NET Framework SDK を参照してください。  
  
### <a name="safe"></a>SAFE  
 内部コンピューター処理とローカル データのアクセスだけが許可されます。 `SAFE` は最も制限が厳しい権限セットです。 `SAFE` 権限が設定されているアセンブリで実行されるコードは、ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスできません。  
  
 `SAFE` アセンブリには、次の権限および値が含まれます。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|`SecurityPermission`|`Execution:` マネージド コードを実行する権限です。|  
|`SqlClientPermission`|`Context connection = true`、`context connection = yes`: context-connection のみを使用できます。接続文字列に指定できる値は、"context connection=true" または "context connection=yes" だけです。<br /><br /> **Allow空白パスワード = false:** 空のパスワードは許可されていません。|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS アセンブリは、アセンブリと同じアクセス許可を持ち、 `SAFE` ファイル、ネットワーク、環境変数、レジストリなどの外部システムリソースにアクセスする機能が追加されています。  
  
 `EXTERNAL_ACCESS` アセンブリには、次の権限および値も含まれます。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|`DistributedTransactionPermission`|`Unrestricted:`分散トランザクションは許可されます。|  
|`DNSPermission`|`Unrestricted:`ドメインネームサーバーから情報を要求するアクセス許可。|  
|`EnvironmentPermission`|`Unrestricted:` システム環境変数およびユーザー環境変数への完全アクセスが許可されます。|  
|`EventLogPermission`|`Administer:` イベント ソースの作成、既存ログの読み取り、イベント ソースまたはログの削除、エントリに対する応答、イベント ログの消去、イベントの待機、およびすべてのイベント ログのコレクションへのアクセスが許可されます。|  
|`FileIOPermission`|`Unrestricted:` ファイルおよびフォルダーへの完全アクセスが許可されます。|  
|`KeyContainerPermission`|`Unrestricted:` キー コンテナーへの完全アクセスが許可されます。|  
|`NetworkInformationPermission`|`Access:` ping の実行が許可されます。|  
|`RegistryPermission`|`HKEY_CLASSES_ROOT`、`HKEY_LOCAL_MACHINE`、`HKEY_CURRENT_USER`、`HKEY_CURRENT_CONFIG`、および `HKEY_USERS.` への読み取り権限が許可されます。|  
|`SecurityPermission`|`Assertion:` このコードのすべての呼び出し元が操作に必要な権限を持っていることをアサートする機能です。<br /><br /> `ControlPrincipal:` プリンシパル オブジェクトを操作する機能です。<br /><br /> `Execution:` マネージド コードを実行する権限です。<br /><br /> `SerializationFormatter:` シリアル化サービスを提供する機能です。|  
|**SmtpPermission**|`Access:` SMTP ホストの 25 番ポートへの発信接続が許可されます。|  
|`SocketPermission`|`Connect:` トランスポート アドレスでの発信接続 (すべてのポートおよびプロトコル) が許可されます。|  
|`SqlClientPermission`|`Unrestricted:` データ ソースへの完全アクセスが許可されます。|  
|`StorePermission`|`Unrestricted:` X.509 証明書ストアへの完全アクセスが許可されます。|  
|`WebPermission`|`Connect:` Web リソースへの発信接続が許可されます。|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE では、アセンブリから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の内外のリソースにも無制限にアクセスできます。 `UNSAFE` アセンブリ内からコードを実行することによって、アンマネージ コードを呼び出すこともできます。  
  
 `UNSAFE` アセンブリには、`FullTrust` が与えられます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 外部のリソースにアクセスせずにコンピューター処理やデータ管理タスクを実行するアセンブリには、`SAFE` 権限を設定することをお勧めします。 `EXTERNAL_ACCESS`既定でサービスアカウントとして実行さ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `EXTERNAL_ACCESS` れるアセンブリは、サービスアカウントとして実行するために信頼されているログインにのみ付与する必要があります。 セキュリティの点では、`EXTERNAL_ACCESS` アセンブリと `UNSAFE` アセンブリに変わりはありません。 ただし、`EXTERNAL_ACCESS` アセンブリには、`UNSAFE` アセンブリにはない、信頼性や堅牢性を目的としたさまざまな保護機能が備わっています。 を指定 `UNSAFE` すると、アセンブリ内のコードはに対して無効な操作を実行でき [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。 で CLR アセンブリを作成する方法の詳細につい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ては、「 [Clr 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)」を参照してください。  
  
## <a name="accessing-external-resources"></a>外部リソースへのアクセス  
 UDT (ユーザー定義型)、ストアド プロシージャ、または他の種類のコンストラクト アセンブリを `SAFE` 権限セットで登録すると、コンストラクト内で実行しているマネージド コードから外部リソースにアクセスできなくなります。 `EXTERNAL_ACCESS` または `UNSAFE` のいずれかの権限セットを指定し、マネージド コードから外部リソースにアクセスする場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって次の規則が適用されます。  
  
|状況|THEN|  
|--------|----------|  
|実行コンテキストが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインに対応している場合。|外部リソースへのアクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していると同時に、本来の呼び出し元である場合。|外部リソースへのアクセスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストで行われます。|  
|呼び出し元が、本来の呼び出し元ではない場合。|アクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していて、実行コンテキストが本来の呼び出し元であり、呼び出し元の権限が借用されている場合。|アクセスにはサービス アカウントではなく、呼び出し元のセキュリティ コンテキストが使用されます。|  
  
## <a name="permission-set-summary"></a>権限セットの概要  
 次の表は、`SAFE`、`EXTERNAL_ACCESS`、および `UNSAFE` の各権限セットに付与される制限事項と権限を示しています。  
  
|||||  
|-|-|-|-|  
||`SAFE`|`EXTERNAL_ACCESS`|`UNSAFE`|  
|`Code Access Security Permissions`|実行のみ|実行および外部リソースへのアクセス|無制限 (P/Invoke を含む)|  
|`Programming model restrictions`|[はい]|はい|制限事項なし|  
|`Verifiability requirement`|[はい]|はい|いいえ|  
|`Local data access`|はい|はい|はい|  
|`Ability to call native code`|いいえ|いいえ|はい|  
  
## <a name="see-also"></a>参照  
 [CLR 統合のセキュリティ](clr-integration-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [CLR 統合プログラミングモデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [CLR ホスト環境](../clr-integration-architecture-clr-hosted-environment.md)  
  
  
