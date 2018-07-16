---
title: CLR 統合のコード アクセス セキュリティ |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
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
caps.latest.revision: 28
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 87b58d73233cf586ec631e43ad17cb9232d59f8f
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37357664"
---
# <a name="clr-integration-code-access-security"></a>CLR 統合のコード アクセス セキュリティ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  共通言語ランタイム (CLR) では、マネージド コードに対してコード アクセス セキュリティというセキュリティ モデルがサポートされます。 このモデルでは、コードの ID に基づいてアセンブリに権限が許可されます。 詳細については、.NET Framework Software Development Kit の「コード アクセス セキュリティ」を参照してください。  
  
 アセンブリに許可される権限を決定するセキュリティ ポリシーは、次の 3 つに分類されます。  
  
-   コンピューター ポリシー : [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がインストールされているコンピューターで実行されるすべてのマネージド コードに対して効力を持つポリシーです。  
  
-   ユーザー ポリシー : 特定のプロセスをホストとするマネージド コードに対して効力を持つポリシーです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の場合、ユーザー ポリシーは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスを実行している Windows アカウントに対して固有になります。  
  
-   ホスト ポリシー : CLR のホスト (この場合は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) によって設定され、そのホストで実行されるマネージド コードに対して効力を持つポリシーです。  
  
 CLR でサポートされるコード アクセス セキュリティ メカニズムは、ランタイムが完全に信頼されるコードと部分的に信頼されるコードの両方をホストできるという前提に基づいています。 CLR コード アクセス セキュリティで保護されるリソースは、通常、そのリソースへのアクセスを許可する前に適切な権限を必要とするマネージド アプリケーション プログラミング インターフェイスによってラップされます。 権限の要求は、(アセンブリ レベルで) 呼び出し履歴内のすべての呼び出し側が、対応するリソース権限を持つ場合にのみ満たされます。  
  
 マネージド コードを [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 内部で実行する際に許可されるコード アクセス セキュリティ権限のセットは、上記の 3 つのポリシー レベルで許可される権限のセットの共通部分です。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込まれたアセンブリに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が一連の権限を許可しても、最終的にユーザー コードに許可される権限セットは、ユーザー レベルおよびコンピューター レベルのポリシーによってさらに制限されることがあります。  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>SQL Server ホスト ポリシー レベルの権限セット  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシー レベルでアセンブリに許可されるコード アクセス セキュリティ権限のセットは、アセンブリの作成時にどの権限セットを指定するかによって決定されます。 次の 3 つのアクセス許可セットがある:**セーフ**、 **EXTERNAL_ACCESS**と**UNSAFE** (を使用して指定、 **PERMISSION_SET** のオプション[アセンブリを作成&#40;TRANSACT-SQL&#41;](../../../t-sql/statements/create-assembly-transact-sql.md))。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、CLR のホスト時に、ホスト レベルのセキュリティ ポリシー レベルを提供します。このポリシーは、常に効力を持つ 2 つのポリシー レベルより下位の追加ポリシー レベルになります。 このポリシーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によって作成されるアプリケーション ドメインごとに設定されます。 このポリシーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が CLR のインスタンスを作成するときに有効になる、既定のアプリケーション ドメイン用ではありません。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト レベル ポリシーは、システム アセンブリの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固定ポリシーと、ユーザー アセンブリのユーザー指定ポリシーの組み合わせです。  
  
 CLR アセンブリと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] システム アセンブリの固定ポリシーでは、これらのアセンブリを完全に信頼します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシーのユーザー指定部分は、アセンブリの所有者がアセンブリごとに指定する 3 つの権限バケットのいずれかに基づきます。 次に示すセキュリティ権限の詳細については、.NET Framework SDK を参照してください。  
  
### <a name="safe"></a>SAFE  
 内部コンピューター処理とローカル データのアクセスだけが許可されます。 **安全な**は最も制限の厳しい権限セットです。 持つアセンブリによって実行されるコード**セーフ**アクセス許可がファイル、ネットワーク、環境変数、またはレジストリなどの外部システム リソースにアクセスできません。  
  
 **安全な**アセンブリは、次の権限および値があります。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|**SecurityPermission**|**実行:** マネージ コードを実行する権限。|  
|**SqlClientPermission**|**コンテキスト接続 = true**、**コンテキスト接続 = [はい]**: のみコンテキスト接続を使用し、接続文字列は、の値を指定できますのみ"コンテキスト接続 = true"または"コンテキスト接続 = [はい]"。<br /><br /> **AllowBlankPassword = false:** 空白のパスワードは許可されていません。|  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS アセンブリと同じアクセス許可がある**セーフ**アセンブリ、追加ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスすることができます。  
  
 **EXTERNAL_ACCESS**アセンブリは、次の権限および値もあります。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**無制限の:** 分散トランザクションが許可されます。|  
|**コード**|**無制限の:** ドメイン ネーム サーバーから情報を要求するアクセス許可。|  
|**EnvironmentPermission**|**無制限の:** 完全なシステムおよびユーザーの環境変数へのアクセスを許可します。|  
|**EventLogPermission**|**管理:** 次の操作を許可する: イベント ソースまたはログをオフにすると、イベントをリッスンして、すべてのイベント ログのコレクションへのアクセスのイベント ログ エントリに対する応答を削除する既存のログを読み取るイベント ソースを作成します。|  
|**FileIOPermission**|**無制限:** ファイルへのフル アクセス、フォルダーを許可します。|  
|**KeyContainerPermission**|**無制限の:** 完全なキー コンテナーへのアクセスを許可します。|  
|**NetworkInformationPermission**|**アクセス:** Pinging が許可されます。|  
|**RegistryPermission**|読み取り権限を許可**HKEY_CLASSES_ROOT**、 **HKEY_LOCAL_MACHINE**、 **HKEY_CURRENT_USER**、 **HKEY_CURRENT_CONFIG**、および**HKEY_USERS します。**|  
|**SecurityPermission**|**アサーション:** このコードのすべての呼び出し元に、操作に必要な権限があることをアサートする機能。<br /><br /> **ControlPrincipal:** プリンシパル オブジェクトを操作する機能。<br /><br /> **実行:** マネージ コードを実行する権限。<br /><br /> **:** シリアル化サービスを提供する機能。|  
|**SmtpPermission**|**アクセス:** SMTP ホスト ポート 25 への発信接続を許可します。|  
|**SocketPermission**|**接続:** トランスポート アドレスで送信接続 (すべてのポートおよびプロトコル) が許可されます。|  
|**SqlClientPermission**|**無制限の:** 完全なデータ ソースへのアクセスを許可します。|  
|**StorePermission**|**無制限:** フル アクセスを X.509 証明書ストアを許可します。|  
|**WebPermission**|**接続:** web リソースへの発信接続を許可します。|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE では、アセンブリから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の内外のリソースにも無制限にアクセスできます。 内から実行されるコード、 **UNSAFE**アセンブリはアンマネージ コードを呼び出すこともできます。  
  
 **安全でない**アセンブリが指定された**FullTrust**します。  
  
> [!IMPORTANT]  
>  **安全な**の外部リソースにアクセスせずに演算とデータ管理タスクを実行するアセンブリの推奨されるアクセス許可の設定は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 **EXTERNAL_ACCESS**外部リソースにアクセスするアセンブリをお勧め[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 **EXTERNAL_ACCESS**として既定ではアセンブリの実行、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービス アカウント。 可能性があります**EXTERNAL_ACCESS**コードを明示的に呼び出し元の Windows 認証セキュリティ コンテキストを偽装します。 既定値は、として実行するため、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービス アカウントを実行する権限**EXTERNAL_ACCESS**のみサービス アカウントとして実行されているログインに与える必要があります。 セキュリティの観点から**EXTERNAL_ACCESS**と**UNSAFE**アセンブリは同じです。 ただし、 **EXTERNAL_ACCESS**アセンブリに追加されていないさまざまな信頼性と堅牢性の保護を提供する**UNSAFE**アセンブリ。 指定する**UNSAFE**に対して無効な操作を実行するアセンブリでコードをできるように、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]領域を処理し、したがって侵害する可能性、堅牢性とスケーラビリティの[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。 CLR アセンブリの作成の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[CLR 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)します。  
  
## <a name="accessing-external-resources"></a>外部リソースへのアクセス  
 ユーザー定義型 (UDT)、ストアド プロシージャ、またはその他の種類のコンストラクト アセンブリに登録されている場合、**セーフ**アクセス許可を設定し、コンストラクトで実行されるマネージ コードでは外部リソースにアクセスできません。 ただし、いずれか、 **EXTERNAL_ACCESS**または**UNSAFE**アクセス許可セットが指定され、マネージ コードが、外部のリソースにアクセスしようとしています。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、次の規則が適用されます。  
  
|状況|そうしたら|  
|--------|----------|  
|実行コンテキストが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインに対応している場合。|外部リソースへのアクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していると同時に、本来の呼び出し元である場合。|外部リソースへのアクセスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストで行われます。|  
|呼び出し元が、本来の呼び出し元ではない場合。|アクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していて、実行コンテキストが本来の呼び出し元であり、呼び出し元の権限が借用されている場合。|アクセスにはサービス アカウントではなく、呼び出し元のセキュリティ コンテキストが使用されます。|  
  
## <a name="permission-set-summary"></a>権限セットの概要  
 次のグラフに与えられた権限と制限を示して、**セーフ**、 **EXTERNAL_ACCESS**、および**UNSAFE**アクセス許可セット。  
  
|||||  
|-|-|-|-|  
||**SAFE**|**EXTERNAL_ACCESS**|**UNSAFE**|  
|**コード アクセス セキュリティ アクセス許可**|実行のみ|実行および外部リソースへのアクセス|無制限 (P/Invoke を含む)|  
|**プログラミング モデルの制限**|はい|はい|制限なし|  
|**検証の必要性**|はい|はい|いいえ|  
|**ローカル データ アクセス**|はい|はい|はい|  
|**ネイティブ コードを呼び出す機能**|いいえ|いいえ|はい|  
  
## <a name="see-also"></a>参照  
 [CLR 統合のセキュリティ](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [CLR 統合プログラミング モデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [CLR ホスト環境](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
