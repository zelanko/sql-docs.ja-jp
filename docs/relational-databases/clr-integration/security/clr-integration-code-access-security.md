---
title: "CLR 統合のコード アクセス セキュリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1bdecb5570f4c139fd42a77d2ef5479758bdf63a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="clr-integration-code-access-security"></a>CLR 統合のコード アクセス セキュリティ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]共通言語ランタイム (CLR) は、マネージ コードに対してコード アクセス セキュリティというセキュリティ モデルをサポートします。 このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。 詳細については、.NET Framework Software Development Kit の「コード アクセス セキュリティ」を参照してください。  
  
 アセンブリに許可される権限を決定するセキュリティ ポリシーは、次の 3 つに分類されます。  
  
-   コンピューター ポリシー : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がインストールされているコンピューターで実行されるすべてのマネージ コードに対して効力を持つポリシーです。  
  
-   ユーザー ポリシー : 特定のプロセスをホストとするマネージ コードに対して効力を持つポリシーです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の場合、ユーザー ポリシーは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスを実行している Windows アカウントに対して固有になります。  
  
-   ホスト ポリシー : CLR のホスト (この場合は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) によって設定され、そのホストで実行されるマネージ コードに対して効力を持つポリシーです。  
  
 CLR でサポートされるコード アクセス セキュリティ メカニズムは、ランタイムが完全に信頼されるコードと部分的に信頼されるコードの両方をホストできるという前提に基づいています。 CLR コード アクセス セキュリティで保護されるリソースは、通常、そのリソースへのアクセスを許可する前に適切な権限を必要とするマネージ アプリケーション プログラミング インターフェイスによってラップされます。 権限の要求は、(アセンブリ レベルで) 呼び出し履歴内のすべての呼び出し側が、対応するリソース権限を持つ場合にのみ満たされます。  
  
 マネージ コードを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部で実行する際に許可されるコード アクセス セキュリティ権限のセットは、上記の 3 つのポリシー レベルで許可される権限のセットの共通部分です。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込まれたアセンブリに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が一連の権限を許可しても、最終的にユーザー コードに許可される権限セットは、ユーザー レベルおよびコンピューター レベルのポリシーによってさらに制限されることがあります。  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>SQL Server ホスト ポリシー レベルの権限セット  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシー レベルでアセンブリに許可されるコード アクセス セキュリティ権限のセットは、アセンブリの作成時にどの権限セットを指定するかによって決定されます。 次の 3 つのアクセス許可セットが生成されます:**セーフ**、 **EXTERNAL_ACCESS**と**UNSAFE** (を使用して指定、 **PERMISSION_SET** のオプション[アセンブリ &#40; を作成します。TRANSACT-SQL と #41 です。](../../../t-sql/statements/create-assembly-transact-sql.md)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、CLR のホスト時に、ホスト レベルのセキュリティ ポリシー レベルを提供します。このポリシーは、常に効力を持つ 2 つのポリシー レベルより下位の追加ポリシー レベルになります。 このポリシーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によって作成されるアプリケーション ドメインごとに設定されます。 このポリシーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が CLR のインスタンスを作成するときに有効になる、既定のアプリケーション ドメイン用ではありません。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト レベル ポリシーは、システム アセンブリの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固定ポリシーと、ユーザー アセンブリのユーザー指定ポリシーの組み合わせです。  
  
 CLR アセンブリと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] システム アセンブリの固定ポリシーでは、これらのアセンブリを完全に信頼します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシーのユーザー指定部分は、アセンブリの所有者がアセンブリごとに指定する 3 つの権限バケットのいずれかに基づきます。 次に示すセキュリティ権限の詳細については、.NET Framework SDK を参照してください。  
  
### <a name="safe"></a>SAFE  
 内部コンピューター処理とローカル データのアクセスだけが許可されます。 **安全な**最も制限の厳しい権限セットです。 持つアセンブリによって実行されるコード**セーフ**アクセス許可がファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスできません。  
  
 **安全な**アセンブリは、次のアクセス許可と値があります。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|**SecurityPermission**|**実行する場合:**をマネージ コードを実行する権限です。|  
|**Sqlclientpermission を与える**|**コンテキスト接続 = true**、**コンテキスト接続 = [はい]**: コンテキスト接続を使用して、接続文字列がの値を指定できますのみ専用"コンテキスト接続 = true"または"コンテキスト接続 = [はい]"です。<br /><br /> **AllowBlankPassword = false:**空のパスワードは許可されていません。|  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS アセンブリと同じアクセス許可がある**セーフ**アセンブリ、ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスする追加機能を使用します。  
  
 **EXTERNAL_ACCESS**アセンブリは、次の権限および値にもあります。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**無制限:**分散トランザクションが許可されます。|  
|**コード**|**無制限:**ドメイン ネーム サーバーから情報を要求するアクセス許可。|  
|**EnvironmentPermission**|**無制限:**完全システムとユーザーの環境変数へのアクセスを許可します。|  
|**EventLogPermission**|**管理:**次の操作が許可されます: イベント ソースまたはオフにすると、イベントをリッスンしていると、すべてのイベント ログのコレクションへのアクセスのイベント ログ エントリに応答して、ログを削除すると、既存のログの読み取り、イベント ソースを作成します。|  
|**FileIOPermission**|**無制限:**ファイルへのフル アクセスのフォルダーが許可されているとします。|  
|**KeyContainerPermission**|**無制限:**フル キー コンテナーへのアクセスを許可します。|  
|**NetworkInformationPermission**|**アクセス:** Pinging は許可されています。|  
|**RegistryPermission**|読み取り権限を許可**HKEY_CLASSES_ROOT**、 **HKEY_LOCAL_MACHINE**、 **HKEY_CURRENT_USER**、 **HKEY_CURRENT_CONFIG**、および**HKEY_USERS です。**|  
|**SecurityPermission**|**アサーション:**このコードのすべての呼び出し元に、操作に必要な権限があることをアサートする機能。<br /><br /> **ControlPrincipal:**プリンシパル オブジェクトを操作する機能。<br /><br /> **実行する場合:**をマネージ コードを実行する権限です。<br /><br /> **SerializationFormatter:**をシリアル化サービスを提供する機能。|  
|**SmtpPermission**|**アクセス:** SMTP ホスト ポート 25 への発信接続を許可します。|  
|**SocketPermission**|**接続:**トランスポート アドレスでの発信接続 (すべてのポートおよびプロトコル) を許可します。|  
|**Sqlclientpermission を与える**|**無制限:**完全データ ソースへのアクセスを許可します。|  
|**StorePermission**|**無制限:**フル アクセスを X.509 証明書ストアを許可します。|  
|**WebPermission**|**接続:** web リソースへの発信接続を許可します。|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE では、アセンブリから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の内外のリソースにも無制限にアクセスできます。 コードを内から実行する、 **UNSAFE**アセンブリでは、アンマネージ コードを呼び出すこともできます。  
  
 **安全でない**アセンブリが指定された**FullTrust**です。  
  
> [!IMPORTANT]  
>  **安全な**外部のリソースにアクセスしなくても計算やデータ管理タスクを実行するアセンブリに推奨されるアクセス許可の設定は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 **EXTERNAL_ACCESS**外部リソースにアクセスするアセンブリをお勧め[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]です。 **EXTERNAL_ACCESS**として既定ではアセンブリの実行、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービス アカウント。 可能であれば**EXTERNAL_ACCESS**呼び出し元の Windows 認証のセキュリティ コンテキストを明示的に借用するためのコード。 既定値は、として実行するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービス アカウントを実行する権限**EXTERNAL_ACCESS**をサービス アカウントとして実行されているログインだけ指定する必要があります。 セキュリティの観点から**EXTERNAL_ACCESS**と**UNSAFE**アセンブリが同一です。 ただし、 **EXTERNAL_ACCESS**アセンブリに追加されていない各種の信頼性と堅牢性の保護を提供する**UNSAFE**アセンブリ。 指定する**UNSAFE**に対して無効な操作を実行するアセンブリにコードをできるように、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]プロセス領域、およびため可能性のある、堅牢性とスケーラビリティを損なうの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 CLR アセンブリの作成の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[CLR 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)です。  
  
## <a name="accessing-external-resources"></a>外部リソースへのアクセス  
 ユーザー定義型 (UDT)、ストアド プロシージャ、またはその他の種類のコンストラクト アセンブリに登録されている場合、**セーフ**アクセス許可を設定し、コンストラクトで実行されるマネージ コードでは外部リソースにアクセスできません。 ただし、いずれか、 **EXTERNAL_ACCESS**または**UNSAFE**権限セットを指定し、マネージ コードが、外部のリソースにアクセスしようとしています。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]次の規則が適用されます。  
  
|状況|そうしたら|  
|--------|----------|  
|実行コンテキストが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインに対応している場合。|外部リソースへのアクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していると同時に、本来の呼び出し元である場合。|外部リソースへのアクセスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストで行われます。|  
|呼び出し元が、本来の呼び出し元ではない場合。|アクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していて、実行コンテキストが本来の呼び出し元であり、呼び出し元の権限が借用されている場合。|アクセスにはサービス アカウントではなく、呼び出し元のセキュリティ コンテキストが使用されます。|  
  
## <a name="permission-set-summary"></a>権限セットの概要  
 次の表では、制限事項およびに付与された権限をまとめたものです、**セーフ**、 **EXTERNAL_ACCESS**、および**UNSAFE**アクセス許可セット。  
  
|||||  
|-|-|-|-|  
||**セーフ**|**EXTERNAL_ACCESS**|**安全でないです。**|  
|**コード アクセス セキュリティのアクセス許可**|実行のみ|実行および外部リソースへのアクセス|無制限 (P/Invoke を含む)|  
|**プログラミング モデルの制限**|可|可|制限はありません。|  
|**検証の必要性**|可|可|不可|  
|**ローカル データ アクセス**|可|可|可|  
|**ネイティブ コードを呼び出すための機能**|不可|いいえ|可|  
  
## <a name="see-also"></a>参照  
 [CLR 統合のセキュリティ](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [CLR 統合プログラミング モデルの制限](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [CLR ホスト環境](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
