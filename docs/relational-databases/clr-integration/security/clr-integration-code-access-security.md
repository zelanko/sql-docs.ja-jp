---
title: CLR 統合コード アクセス セキュリティ |マイクロソフトドキュメント
description: SQL Server CLR 統合では、CLR はマネージ コードのコード アクセス セキュリティをサポートします。
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
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
ms.openlocfilehash: 912db3acb6f6dc21952e99da31a1484a9745ed0b
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488313"
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
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシー レベルでアセンブリに許可されるコード アクセス セキュリティ権限のセットは、アセンブリの作成時にどの権限セットを指定するかによって決定されます。 アクセス許可セットには **、SAFE** **、EXTERNAL_ACCESS、****および UNSAFE**の 3 つのアクセス許可セットがあります[([アセンブリの作成] &#40;Transact-SQL&#41;](../../../t-sql/statements/create-assembly-transact-sql.md)の**PERMISSION_SET**オプションを使用して指定します)。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、CLR のホスト時に、ホスト レベルのセキュリティ ポリシー レベルを提供します。このポリシーは、常に効力を持つ 2 つのポリシー レベルより下位の追加ポリシー レベルになります。 このポリシーは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によって作成されるアプリケーション ドメインごとに設定されます。 このポリシーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が CLR のインスタンスを作成するときに有効になる、既定のアプリケーション ドメイン用ではありません。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト レベル ポリシーは、システム アセンブリの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固定ポリシーと、ユーザー アセンブリのユーザー指定ポリシーの組み合わせです。  
  
 CLR アセンブリと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] システム アセンブリの固定ポリシーでは、これらのアセンブリを完全に信頼します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ホスト ポリシーのユーザー指定部分は、アセンブリの所有者がアセンブリごとに指定する 3 つの権限バケットのいずれかに基づきます。 次に示すセキュリティ権限の詳細については、.NET Framework SDK を参照してください。  
  
### <a name="safe"></a>SAFE  
 内部コンピューター処理とローカル データのアクセスだけが許可されます。 **SAFE**は、最も制限の厳しいアクセス許可セットです。 **SAFE**アクセス許可を持つアセンブリによって実行されるコードは、ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスできません。  
  
 **SAFE**アセンブリには、次のアクセス許可と値があります。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|**SecurityPermission**|**実行:** マネージ コードを実行するアクセス許可。|  
|**SqlClientPermission**|**コンテキスト接続 = true**、**コンテキスト接続 = yes**: コンテキスト接続のみを使用でき、接続文字列は "コンテキスト接続=true" または "コンテキスト接続=yes" の値のみを指定できます。<br /><br /> **許可空白パスワード = 偽:** 空白のパスワードは許可されません。|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS アセンブリには、ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにアクセスする追加の機能を備えた **、SAFE**アセンブリと同じアクセス許可があります。  
  
 **EXTERNAL_ACCESS**アセンブリには、次のアクセス許可と値も含まれます。  
  
|権限|値/説明|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**無制限:** 分散トランザクションは許可されます。|  
|**DNS アクセス許可**|**無制限:** ドメイン ネーム サーバーに情報を要求するアクセス許可。|  
|**EnvironmentPermission**|**無制限:** システム環境変数およびユーザー環境変数へのフルアクセスが許可されます。|  
|**EventLogPermission**|**管理:** イベント ソースの作成、既存のログの読み取り、イベント ソースまたはログの削除、エントリへの応答、イベント ログのクリア、イベントのリッスン、およびすべてのイベント ログのコレクションへのアクセスの操作を実行できます。|  
|**FileIOPermission**|**無制限:** ファイルおよびフォルダへのフル アクセスが許可されます。|  
|**KeyContainerPermission**|**無制限:** キー コンテナーへのフル アクセスが許可されます。|  
|**NetworkInformationPermission**|**アクセス:** ping は許可されています。|  
|**RegistryPermission**|**HKEY_CLASSES_ROOT**、 **HKEY_LOCAL_MACHINE**、 **HKEY_CURRENT_USER**、 **HKEY_CURRENT_CONFIG**、および HKEY_USERS に対する読み取り権限を許可します **。**|  
|**SecurityPermission**|**アサーション:** このコードのすべての呼び出し元が、操作に必要なアクセス許可を持っていることをアサートする機能。<br /><br /> **コントロールプリンシパル:** プリンシパル オブジェクトを操作する機能。<br /><br /> **実行:** マネージ コードを実行するアクセス許可。<br /><br /> **シリアル化フォーマッタ:** シリアル化サービスを提供する機能。|  
|**SmtpPermission**|**アクセス:** SMTP ホスト ポート 25 への送信接続が許可されます。|  
|**SocketPermission**|**接続:** トランスポート アドレス上の送信接続 (すべてのポート、すべてのプロトコル) が許可されます。|  
|**SqlClientPermission**|**無制限:** データ ソースへのフル アクセスが許可されます。|  
|**StorePermission**|**無制限:** X.509 証明書ストアへのフル アクセスが許可されます。|  
|**WebPermission**|**接続:** Web リソースへの送信接続は許可されます。|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE では、アセンブリから [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の内外のリソースにも無制限にアクセスできます。 **UNSAFE**アセンブリ内から実行されるコードは、アンマネージ コードを呼び出すこともできます。  
  
 **安全でない**アセンブリには **、完全信頼**が与えられます。  
  
> [!IMPORTANT]  
>  **SAFE**は、外部[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のリソースにアクセスせずに計算タスクおよびデータ管理タスクを実行するアセンブリに対して推奨されるアクセス許可設定です。 **EXTERNAL_ACCESS**は、外部[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のリソースにアクセスするアセンブリに対して推奨されます。 **既定**では、EXTERNAL_ACCESSアセンブリはサービス[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]アカウントとして実行されます。 **EXTERNAL_ACCESSコード**は、呼び出し元の Windows 認証セキュリティ コンテキストを明示的に偽装できます。 既定では[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サービス アカウントとして実行されるため **、EXTERNAL_ACCESS**実行するアクセス許可は、サービス アカウントとして実行するために信頼されているログインにのみ与える必要があります。 セキュリティの観点から **、EXTERNAL_ACCESS**アセンブリと**UNSAFE**アセンブリは同じです。 ただし **、EXTERNAL_ACCESS**アセンブリは **、UNSAFE**アセンブリにはないさまざまな信頼性と堅牢性の保護を提供します。 **UNSAFE**を指定すると、アセンブリ内のコードはプロセス空間に対[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]して不正な操作を実行できるため、の堅牢性とスケーラビリティが損[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]なわれる可能性があります。 CLR アセンブリの作成の詳細については、「 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [CLR 統合アセンブリの管理](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)」を参照してください。  
  
## <a name="accessing-external-resources"></a>外部リソースへのアクセス  
 ユーザー定義型 (UDT)、ストアド プロシージャ、またはその他の種類のコンストラクト アセンブリが**SAFE**アクセス許可セットに登録されている場合、そのコンストラクトで実行されているマネージ コードは外部リソースにアクセスできません。 ただし **、EXTERNAL_ACCESS**または**UNSAFE**アクセス許可セットが指定され、マネージ コードが外部リソースにアクセスしようとすると[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、次の規則が適用されます。  
  
|状況|THEN|  
|--------|----------|  
|実行コンテキストが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインに対応している場合。|外部リソースへのアクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していると同時に、本来の呼び出し元である場合。|外部リソースへのアクセスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストで行われます。|  
|呼び出し元が、本来の呼び出し元ではない場合。|アクセスが拒否され、セキュリティ例外が発生します。|  
|実行コンテキストが Windows ログインに対応していて、実行コンテキストが本来の呼び出し元であり、呼び出し元の権限が借用されている場合。|アクセスにはサービス アカウントではなく、呼び出し元のセキュリティ コンテキストが使用されます。|  
  
## <a name="permission-set-summary"></a>権限セットの概要  
 次の表は **、SAFE** **、EXTERNAL_ACCESS、****および UNSAFE**アクセス許可セットに付与される制限とアクセス許可をまとめたものです。  
  
|||||  
|-|-|-|-|  
||**SAFE**|**EXTERNAL_ACCESS**|**Unsafe**|  
|**コード アクセス セキュリティのアクセス許可**|実行のみ|実行および外部リソースへのアクセス|無制限 (P/Invoke を含む)|  
|**プログラミング モデルの制限事項**|はい|はい|無制限|  
|**検証可能性の要件**|はい|はい|いいえ|  
|**ローカル データ アクセス**|はい|はい|はい|  
|**ネイティブ コードを呼び出す機能**|いいえ|いいえ|はい|  
  
## <a name="see-also"></a>参照  
 [CLR 統合セキュリティ](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [ホスト保護属性と CLR 統合プログラミング](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [CLR 統合プログラミング モデルの制限事項](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [CLR ホスト環境](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
