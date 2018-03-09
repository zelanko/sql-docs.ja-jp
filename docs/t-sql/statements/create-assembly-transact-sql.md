---
title: "アセンブリ (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 8/07/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASSEMBLY
- CREATE ASSEMBLY
- CREATE_ASSEMBLY_TSQL
- ASSEMBLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- assemblies [CLR integration], validating
- validating assemblies
- CREATE ASSEMBLY statement
- assemblies [CLR integration], creating
ms.assetid: d8d1d245-c2c3-4325-be52-4fc1122c2079
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3f937dc219eb317347cceeafcdcd8753244bcb07
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="create-assembly-transact-sql"></a>CREATE ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  クラス メタデータとマネージ コードを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内のオブジェクトとして含む、マネージ アプリケーション モジュールを作成します。 データベース内では、このモジュールを参照することにより、共通言語ランタイム (CLR) 関数、ストアド プロシージャ、トリガー、ユーザー定義集計関数、ユーザー定義型を作成できます。  
  
>  [!WARNING]
>  CLR では、セキュリティ境界としてサポートされなくなった、.NET Framework のコード アクセス セキュリティ (CAS) が使用されます。 `PERMISSION_SET = SAFE` で作成された CLR アセンブリが、外部のシステム リソースにアクセスし、非管理対象コードを呼び出し、sysadmin 特権を取得できる場合があります。 [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] 以降、CLR アセンブリのセキュリティを強化するために `clr strict security` という `sp_configure` オプションが導入されました。 `clr strict security` は既定で有効になり、`SAFE` および `EXTERNAL_ACCESS` アセンブリを `UNSAFE` とマークされている場合と同様に扱います。 `clr strict security` オプションは、旧バージョンとの互換性のために無効にできますが、これは推奨されません。 Microsoft では、master データベースで `UNSAFE ASSEMBLY` アクセス許可が付与されている対応するログインを含む証明書または非対称キーで、すべてのアセンブリに署名することをお勧めします。 詳しくは、「[CLR の厳密なセキュリティ](../../database-engine/configure-windows/clr-strict-security.md)」をご覧ください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE ASSEMBLY assembly_name  
[ AUTHORIZATION owner_name ]  
FROM { <client_assembly_specifier> | <assembly_bits> [ ,...n ] }  
[ WITH PERMISSION_SET = { SAFE | EXTERNAL_ACCESS | UNSAFE } ]  
[ ; ]  
<client_assembly_specifier> :: =  
        '[\\computer_name\]share_name\[path\]manifest_file_name'  
  | '[local_path\]manifest_file_name'  
  
<assembly_bits> :: =  
{ varbinary_literal | varbinary_expression }  
```  
  
## <a name="arguments"></a>引数  
 *assembly_name*  
 アセンブリの名前を指定します。 名前は、データベースと、有効な内で一意である必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 AUTHORIZATION *owner_name*  
 アセンブリの所有者となるユーザーまたはロールの名前を指定します。 *owner_name*うち、現在のユーザーがメンバー、または現在のユーザーでは、に対する IMPERSONATE 権限が必要なロールの名前を指定するかする必要*owner_name*です。 このオプションを指定しない場合は、所有権は現在のユーザーに与えられます。  
  
 \<client_assembly_specifier>  
アップロードされているアセンブリが置かれるローカル パスまたはネットワーク上の位置と、そのアセンブリに対応するマニフェスト ファイル名を指定します。  \<client_assembly_specifier >、固定文字列または変数に、固定文字列に評価される式として表現できます。 CREATE ASSEMBLY では、マルチモジュール アセンブリの読み込みはサポートされません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]同じ場所にこのアセンブリの依存アセンブリの検索し、ルート レベル アセンブリとして、同じ所有者アップロードされます。 これらの依存アセンブリが検出されず、現在のデータベースに読み込まれていない場合、CREATE ASSEMBLY は失敗します。 依存アセンブリが現在のアセンブリに既に読み込まれている場合、これらのアセンブリの所有者は、新しく作成されたアセンブリの所有者と同じであることが必要です。
  
 \<client_assembly_specifier > でログオンしているユーザーが偽装されているかどうかは指定できません。  
  
 \<assembly_bits>  
 アセンブリとその依存アセンブリを構成するバイナリ値のリストを指定します。 リストの最初の値は、ルート レベルのアセンブリとして扱われます。 依存アセンブリに対応する値は、任意の順序で指定できます。 ルート アセンブリの依存関係に対応していない値は無視されます。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 *varbinary_literal*  
 **Varbinary**リテラルです。  
  
 *varbinary_expression*  
 型の式は、 **varbinary**です。  
  
 PERMISSION_SET { **SAFE** | EXTERNAL_ACCESS | UNSAFE }  
 >  [!IMPORTANT]  
 >  `PERMISSION_SET`オプションの影響を受けました、`clr strict security`オプション、opening 警告で説明します。 ときに`clr strict security`が有効になっている、すべてのアセンブリとして扱われます`UNSAFE`です。
 
 使用してアクセスされたときに、アセンブリに与えられているコード アクセス権限のセットを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 指定しない場合、既定値として SAFE が適用されます。  
  
 SAFE を使用することをお勧めします。 SAFE は最も限定的な権限セットです。 SAFE 権限を持つアセンブリによって実行されるコードでは、ファイル、ネットワーク、環境変数、レジストリなどの外部システム リソースにはアクセスできません。  
  
 EXTERNAL_ACCESS を指定した場合、アセンブリでは、ファイル、ネットワーク、環境変数、レジストリなどの特定の外部システム リソースにアクセスできます。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 UNSAFE アセンブリのインスタンスの内外両方のリソースに無制限のアクセスを有効に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 UNSAFE アセンブリ内から実行するコードでは、アンマネージ コードを呼び出すことができます。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
> [!IMPORTANT]  
>  アセンブリで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス外のリソースにアクセスせずに計算やデータ管理タスクを実行する場合は、権限設定として SAFE を使用することをお勧めします。  
>   
>  アセンブリで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス外のリソースにアクセスする場合は、EXTERNAL_ACCESS を使用することをお勧めします。 EXTERNAL_ACCESS アセンブリでは SAFE アセンブリの信頼性とスケーラビリティによる保護が提供されますが、セキュリティの観点からは、このアセンブリは UNSAFE アセンブリと類似しています。 EXTERNAL_ACCESS アセンブリ内のコードは、明示的に呼び出し元の権限を借用しない限り、既定により [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントの下で実行され、外部リソースにアクセスします。 したがって、EXTERNAL_ACCESS アセンブリを作成する権限は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントの下でコードを実行しても安全であると考えられる、信頼できるログインに対してのみ許可してください。 権限借用の詳細については、次を参照してください。 [CLR 統合のセキュリティ](../../relational-databases/clr-integration/security/clr-integration-security.md)です。  
>   
>  UNSAFE を指定した場合、アセンブリのコードでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセス領域に対して自由な操作を実行できるので、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の堅牢性が脅かされる可能性があります。 UNSAFE アセンブリは、いずれかのセキュリティ システムを覆すも可能性があることができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または共通言語ランタイム。 UNSAFE 権限は、信頼性の高いアセンブリに対してのみ許可してください。 メンバーにのみ、 **sysadmin**固定サーバー ロールの作成し、UNSAFE アセンブリを変更できます。  
  
 アセンブリの権限セットの詳細については、次を参照してください。[アセンブリの設計](../../relational-databases/clr-integration/assemblies-designing.md)です。  
  
## <a name="remarks"></a>解説  
 CREATE ASSEMBLY では、.dll ファイルとしてコンパイル済みのアセンブリがマネージ コードからアップロードされ、SQL Server インスタンス内で使用できるようになります。  
 
有効にすると、`CREATE ASSEMBLY` および `ALTER ASSEMBLY` のステートメントの `PERMISSION_SET` オプションが実行時に無視されますが、`PERMISSION_SET` オプションはメタデータに保持されます。 オプションを無視すると、既存のコード ステートメントの改変が最小限に抑えられます。
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、名前、カルチャ、および公開キーが同じでありバージョンが異なるアセンブリの登録を許可していません。  
  
指定されたアセンブリにアクセスしようとしています。 \<client_assembly_specifier >、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]現在の Windows ログインのセキュリティ コンテキストの権限を借用します。 場合\<client_assembly_specifier > ネットワークの場所 (UNC パス) を指定します。 現在のログインの権限の借用が引き継がれませんネットワークの場所に委任制限があり。 この場合、アクセスは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントのセキュリティ コンテキストを使って行われます。 詳細については、次を参照してください。[資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)です。
  
 によって指定されたルート アセンブリだけでなく*assembly_name*、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アップロードされるルート アセンブリによって参照されているすべてのアセンブリをアップロードしようとしています。 参照先のアセンブリが、先に実行された CREATE ASSEMBLY ステートメントにより既にアップロードされている場合、そのアセンブリはアップロードされませんが、ルート アセンブリからは引き続き使用できます。 依存アセンブリがまだアップロードされておらず、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではソース ディレクトリ内にそのアセンブリのマニフェスト ファイルが検出できない場合、CREATE ASSEMBLY ではエラーが返されます。  
  
 ルート アセンブリにより参照される依存アセンブリがデータベースに存在しておらず、ルート アセンブリと一緒に暗黙的に読み込まれる場合、依存アセンブリにはルート レベル アセンブリと同じ権限セットが与えられます。 ルート レベル アセンブリと異なる権限セットを使って依存アセンブリを作成する必要がある場合は、ルート レベル アセンブリより前に、適切な権限セットが与えられた依存アセンブリを明示的にアップロードする必要があります。  
  
## <a name="assembly-validation"></a>アセンブリの検証  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CREATE ASSEMBLY ステートメントによりアップロードされたアセンブリ バイナリに対して、次の点を確認するためのチェックが実行されます。  
  
-   アセンブリ バイナリが有効なメタデータとコード セグメントに基づく整形式になっており、コード セグメントに有効な MSIL (Microsoft Intermediate language) 命令が含まれていること。  
  
-   参照先の一連のシステム アセンブリが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされているアセンブリ (Microsoft.Visualbasic.dll、Mscorlib.dll、System.Data.dll、System.dll、System.Xml.dll、Microsoft.Visualc.dll、Custommarshallers.dll、System.Security.dll、System.Web.Services.dll、System.Data.SqlXml.dll、System.Core.dll、System.Xml.Linq.dll) のいずれか 1 つであること。 他のシステム アセンブリは参照できますが、データベースに明示的に登録されている必要があります。  
  
-   SAFE または EXTERNAL ACCESS 権限セットを使用して作成されるアセンブリの場合は、次の点がチェックされます。  
  
    -   アセンブリ コードが安全な型であること。 型の安全性は、アセンブリに対して共通言語ランタイム ベリファイアを実行することにより確立されます。  
  
    -   読み取り専用とマークされていない静的データ メンバーが、アセンブリのクラス内に含まれていないこと。  
  
    -   アセンブリのクラスに、ファイナライザー メソッドが含まれていないこと。  
  
    -   アセンブリのクラスまたはメソッドの注釈が、許可されているコード属性に基づいて設定されていること。 詳細については、次を参照してください。 [CLR ルーチンのカスタム属性](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)です。  
  
 これらのチェックは CREATE ASSEMBLY の実行時に行われますが、アセンブリ内のコードの実行時には追加のチェックも行われます。  
  
-   特定の呼び出し[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]を特定のコード アクセス権限を必要とする Api は、アセンブリの権限のセットにそのアクセス許可が含まれていない場合に失敗する可能性があります。  
  
-   SAFE と EXTERNAL_ACCESS アセンブリでは、しようとする呼び出し[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]特定の HostProtectionAttributes で注釈が付けられている Api は失敗します。  
  
 詳細については、次を参照してください。[アセンブリの設計](../../relational-databases/clr-integration/assemblies-designing.md)です。  
  
## <a name="permissions"></a>権限  
 CREATE ASSEMBLY 権限が必要です。  
  
 場合 PERMISSION_SET = EXTERNAL_ACCESS を指定する必要がありますと**EXTERNAL ACCESS ASSEMBLY**サーバーに対する権限。 場合 PERMISSION_SET = UNSAFE を指定する必要がありますと**UNSAFE ASSEMBLY**サーバーに対する権限。  
  
 アップロードするアセンブリによって参照されているアセンブリがデータベース内に存在する場合、ユーザーは、この参照先となるアセンブリの所有者であることが必要です。 ファイル パスを使用してアセンブリをアップロードするに、現在のユーザーを、Windows 認証ログインまたはのメンバーである必要があります、 **sysadmin**固定サーバー ロール。 CREATE ASSEMBLY を実行するユーザーの Windows ログインには、共有フォルダーおよびステートメントに読み込まれるファイルに対する読み取り権限が与えられている必要があります。  

### <a name="permissions-with-clr-strict-security"></a>CLR の厳格なセキュリティ アクセス許可    
`CLR strict security` が有効になっている場合に CLR アセンブリを作成するには、次のアクセス許可が必要です。

- ユーザーには `CREATE ASSEMBLY` アクセス許可が必要です  
- さらに、次の条件のいずれかを満たす必要があります。  
  - サーバーでの `UNSAFE ASSEMBLY` アクセス許可のある対応するログインを含む証明書または非対称キーでアセンブリが署名されている。 アセンブリへの署名は推奨されます。  
  - データベースに `ON` に設定された `TRUSTWORTHY` プロパティが含まれ、そのデータベースがサーバーでの `UNSAFE ASSEMBLY` アクセス許可のあるログインによって所有されている。 このオプションは推奨されません。  
  
 アセンブリの権限セットの詳細については、次を参照してください。[アセンブリの設計](../../relational-databases/clr-integration/assemblies-designing.md)です。  
  
## <a name="examples"></a>使用例  
  
### <a name="example-a-creating-an-assembly-from-a-dll"></a>例 a: dll からアセンブリを作成します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の例で、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]サンプルは、ローカル コンピューターの既定の場所にインストールし、HelloWorld.csproj サンプル アプリケーションをコンパイルします。 詳細については、次を参照してください。 [Hello World サンプル](http://msdn.microsoft.com/library/fed6c358-f5ee-4d4c-9ad6-089778383ba7)です。  
  
```  
CREATE ASSEMBLY HelloWorld   
FROM <system_drive>:\Program Files\Microsoft SQL Server\100\Samples\HelloWorld\CS\HelloWorld\bin\debug\HelloWorld.dll  
WITH PERMISSION_SET = SAFE;  
```  
  
### <a name="example-b-creating-an-assembly-from-assembly-bits"></a>例 b: アセンブリ ビットからアセンブリを作成します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 (これは、完全性または有効ではありません)、サンプルのビットをアセンブリ ビットに置き換えます。  
  
```  
CREATE ASSEMBLY HelloWorld  
    FROM 0x4D5A900000000000  
WITH PERMISSION_SET = SAFE;  
```  
  
## <a name="see-also"></a>参照  
 [アセンブリの変更 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [アセンブリ &#40; を削除します。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-assembly-transact-sql.md)   
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [集計 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-aggregate-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [使用シナリオと例については、共通言語ランタイム &#40;です。CLR &#41;統合](http://msdn.microsoft.com/library/33aac25f-abb4-4f29-af88-4a0dacd80ae7)  
  
  
