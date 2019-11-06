---
title: SQL Server Management Studio を使用した Always Encrypted の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.COLUMNMASTERKEY.PAGE.F1
- SQL13.SWB.COLUMNENCRYPTIONKEY.PAGE.F1
- SQL13.SWB.COLUMNMASTERKEY.ROTATION.F1
helpviewer_keywords:
- Always Encrypted, configure with SSMS
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f9ceeb515aa88e3b86be1732ff3f617eea31156c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050027"
---
# <a name="configure-always-encrypted-using-sql-server-management-studio"></a>SQL Server Management Studio を使用した Always Encrypted の構成
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

この記事では、[SQL Server Management Studio (SSMS)](../../../ssms/download-sql-server-management-studio-ssms.md) を使用して Always Encrypted を構成し、Always Encrypted を使用したデータベースを管理するためのタスクについて説明します。

SSMS を使用して Always Encrypted を構成する場合、SSMS によって Always Encrypted のキーと機密データの両方が処理されます。結果、キーとデータは両方とも SSMS プロセス内ではプレーンテキストの形式で表示されます。 したがって、セキュリティで保護されたコンピューターで SSMS を実行することが重要です。 データベースが SQL Server でホストされている場合は、SQL Server インスタンスをホストするコンピューターとは異なるコンピューターで SSMS を実行する必要があります。 Always Encrypted の主な目的は、データベース システムが侵害されても、暗号化された機密データが確実に保護されるようにすることにあるので、SQL Server コンピューター上でキーまたは機密データを処理する PowerShell スクリプトが実行されると、機能の効果が低下したり無効になったりするおそれがあります。 追加の推奨事項については、 [Security Considerations for Key Management](overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management)(キー管理でのセキュリティに関する考慮事項) を参照してください。

SSMS では、データベースを管理する人 (DBA) と、暗号化された機密情報を管理していてプレーンテキスト データへのアクセス権を持つ人 (セキュリティ管理者かアプリケーション管理者または両者) との間でのロールの分離をサポートしていません。 組織でロールの分離が実施される場合は、PowerShell を使用して Always Encrypted を構成する必要があります。 詳細については、「[Always Encrypted のキー管理の概要](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)」および「[PowerShell を使用した Always Encrypted の構成](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)」を参照してください。

## <a name="configuring-always-encrypted-using-the-always-encrypted-wizard"></a>Always Encrypted ウィザードを使用した Always Encrypted の構成

[Always Encrypted ウィザード](../../../relational-databases/security/encryption/always-encrypted-wizard.md) は、選択したデータベースの列に対して目的の暗号化構成を設定することができる強力なツールです。 現在の Always Encrypted の構成と目的のターゲット構成に応じて、ウィザードでは、列を暗号化したり、列の暗号化を解除したり (解読)、列を再暗号化したり (たとえば、列に対して構成された、新しい列暗号化キー、または現在のものとは異なる暗号化の種類を使用) できます。 ウィザードの 1 回の実行で、複数の列を構成することができます。

Always Encrypted に対してキーをプロビジョニングしていない場合は、ウィザードが自動的にキーを生成してくれます。 列マスター キーのキー ストアとして、つぎのどちらかを選択する必要があるだけです:Windows 証明書ストアまたは Azure Key Vault。 ウィザードでは、キーの名前とメタデータ オブジェクトがデータベース内に自動的に生成されます。 キーのプロビジョニング方法をより詳細に制御する必要がある場合 (および列マスター キーを格納したキー ストアの選択肢がもっと必要である場合) は、 **[新しい列マスター キー]** ダイアログと **[新しい列の暗号化キー]** ダイアログ (後で説明) を使用してキーをプロビジョニングしてから、ウィザードを開始してください。 Always Encrypted ウィザードでは、既存の列暗号化キーを選択できます。

このウィザードの使い方の詳細については、  [Always Encrypted ウィザード](../../../relational-databases/security/encryption/always-encrypted-wizard.md)を参照してください。

## <a name="querying-encrypted-columns"></a>暗号化された列のクエリ

このセクションでは、次の作業の方法について説明します。   
-   暗号化された列に格納された暗号化テキスト値を取得する。   
-   暗号化された列に格納されたプレーンテキスト値を取得する。   
-   暗号化された列をターゲットとするプレーンテキスト値を送信する (たとえば、`INSERT` または `UPDATE` ステートメントや、`WHERE` ステートメントの `SELECT` 句のルックアップ パラメーターとして)。

### <a name="retrieving-ciphertext-values-stored-in-encrypted-columns"></a>暗号化された列に格納された暗号化テキスト値の取得    

(値の暗号化を解除せずに) 暗号化テキストとして暗号化された列から値を取得する場合は、次のようにします。
1.  Always Encrypted が、`SELECT` クエリを実行するクエリ エディター ウィンドウでデータベース接続に対して無効になっていることを確認します。 以下の、「 [データベース接続での Always Encrypted の有効化と無効化](#en-dis) 」を参照してください。      
2.  `SELECT` クエリを実行します。 暗号化された列から取得されたデータは、バイナリ (暗号化された) 値として返されます。   

*例*   
`SSN` が `Patients` テーブルの暗号化された列であると仮定して、以下に示されているクエリでバイナリ暗号化テキスト値を取得します (Always Encrypted がデータベース接続で無効になっている場合)。   

![always-encrypted-ciphertext](../../../relational-databases/security/encryption/media/always-encrypted-ciphertext.png)
 
### <a name="retrieving-plaintext-values-stored-in-encrypted-columns"></a>暗号化された列に格納されたプレーンテキスト値の取得    

(値の暗号化を解除するために) プレーンテキストとして暗号化された列から値を取得する場合は、次のようにします。   
1.  Always Encrypted が、`SELECT` クエリを実行するクエリ エディター ウィンドウでデータベース接続に対して有効になっていることを確認します。 これにより、.NET Framework Data Provider for SQL Server (SSMS で使用) に、暗号化された列から取得されたデータの暗号化を解除するよう指示されます。 以下の、「 [データベース接続での Always Encrypted の有効化と無効化](#en-dis) 」を参照してください。
2.  暗号化された列に構成されているすべての列マスター キーにアクセスできることを確認します。 たとえば、列マスター キーが証明書である場合、SSMS が実行されているコンピューターに証明書が展開されていることを確認する必要があります。 あるいは、列マスター キーが Azure Key Vault に格納されているキーの場合、キーにアクセスする権限があることを確認する必要があります (Azure へのサインインが求められる場合もあります)。
3.  `SELECT` クエリを実行します。 暗号化された列から取得されたデータは、元のデータ型の値と同じプレーンテキストとして返されます。   

*例*   
SSN が `char(11)` テーブルで暗号化された `Patients` 列であると仮定して、以下に示されているクエリでプレーンテキスト値を返します (Always Encrypted がデータベース接続で有効になっている場合、および `SSN` 列に構成された列マスター キーにアクセスできる場合)。   

![always-encrypted-plaintext](../../../relational-databases/security/encryption/media/always-encrypted-plaintext.png)
 
### <a name="sending-plaintext-values-targeting-encrypted-columns"></a>暗号化された列をターゲットとするプレーンテキスト値の送信       

暗号化された列をターゲットとする値を送信するクエリ (暗号化された列に格納されている値を使用して挿入、更新またはフィルタリングするクエリなど) を実行する場合は、次のようにします。

1. Always Encrypted が、`SELECT` クエリを実行するクエリ エディター ウィンドウでデータベース接続に対して有効になっていることを確認します。 これにより、.NET Framework Data Provider for SQL Server (SSMS で使用) に、暗号化された列をターゲットとするパラメーター化された Transact-SQL 変数 (以下を参照) を暗号化するよう指示されます。 以下の、「 [データベース接続での Always Encrypted の有効化と無効化](#en-dis) 」を参照してください。
2. 暗号化された列に構成されているすべての列マスター キーにアクセスできることを確認します。 たとえば、列マスター キーが証明書である場合、SSMS が実行されているコンピューターに証明書が展開されていることを確認する必要があります。 あるいは、列マスター キーが Azure Key Vault に格納されているキーの場合、キーにアクセスする権限があることを確認する必要があります (Azure へのサインインが求められる場合もあります)。
3. クエリ エディター ウィンドウで Always Encrypted のパラメーター化が有効になっていることを確認してください。 (SSMS バージョン 17.0 以降が必要です)。Transact-SQL 変数を宣言し、データベースに送信 (挿入、更新またはフィルタリング) する値で初期化します。 詳細については、以下の「 [Always Encrypted のパラメーター化](#param) 」を参照してください。

   > [!NOTE]
   > Always Encrypted でサポートされる型変換のサブセットは限られているため、多くの場合、Transact-SQL 変数のデータ型が、ターゲットとなるターゲット データベース列の型と同じである必要があります。

4. データベースに Transact-SQL 変数の値を送信するクエリを実行します。 SSMS は変数をクエリ パラメーターに変換し、その値を暗号化してからデータベースに送信します。   

*例* `SSN` が `Patients` テーブルの暗号化された `char(11)` 列であると仮定して、以下のスクリプトで SSN 列の `'795-73-9838'` を含む行の検索を試み、`LastName` 列の値を返します (Always Encrypted がデータベース接続で有効で、Always Encrypted のパラメーター化がクエリ エディター ウィンドウで有効で、`SSN` 列に構成された列マスター キーにアクセスできる場合)。   

![always-encrypted-patients](../../../relational-databases/security/encryption/media/always-encrypted-patients.png)

### <a name="en-dis"></a> データベース接続での Always Encrypted の有効化と無効化   

データベース接続で Always Encrypted を有効にすると、以下の操作を透過的に試行するように、SQL Server Management Studio で使用される NET Framework Data Provider for SQL Server に指示されます。   
-   暗号化された列から取得され、クエリ結果に返される値の暗号化を解除する。   
-   暗号化されたデータベース列をターゲットとするパラメーター化された Transact-SQL 変数の値を暗号化する。   
データベース接続で Always Encrypted を有効にするには、 `Column Encryption Setting=Enabled` [サーバーに接続] **ダイアログの** [追加のプロパティ] **タブで** を指定します。    
データベース接続で Always Encrypted を無効にするには、`Column Encryption Setting=Disabled` を指定するか、または **[サーバーに接続]** ダイアログの **[追加のプロパティ]** タブから **[列暗号化設定]** の設定を削除します (既定値は **[無効]** )。   

> [!TIP]
> 既存のクエリ エディター ウィンドウで Always Encrypted の有効化と無効化を切り替えるには、次のようにします。   
> 1.    クエリ エディター ウィンドウの任意の場所をクリックします。
> 2.    **[接続]**  >  **[接続の変更...]** の順に選択します。 
> 3.    **[オプション]** をクリックします。
> 4.    **[追加のプロパティ]** タブを選択し、`Column Encryption Setting=Enabled` を入力する (Always Encrypted の動作を有効にする) か、設定を削除します (Always Encrypted の動作を無効にする)。   
> 5.    **[接続]** をクリックします。   
   
### <a name="param"></a>Always Encrypted のパラメーター化   
 
Always Encrypted のパラメーター化は、Transact-SQL 変数をクエリ パラメーター ([SqlParameter クラス](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.aspx)のインスタンス) に自動的に変換する、SQL Server Management Studio の機能です (SSMS バージョン 17.0 以降が必要です)。これにより、基になる .NET Framework Data Provider for SQL Server は暗号化された列をターゲットとするデータを検出し、データベースに送信する前にそのデータを暗号化できます。 
  
パラメーター化しないと、.NET Framework Data Provider は、クエリ エディターで作成される各ステートメントを非パラメーター化クエリとして渡します。 クエリに、暗号化された列をターゲットとする Transact-SQL 変数またはリテラルが含まれている場合、.NET Framework Data Provider for SQL Server では、データベースにクエリを送信する前に、データを検出して暗号化することはできません。 その結果、(プレーンテキストのリテラル Transact-SQL 変数と暗号化された列の間で) 型が一致しないため、クエリは失敗します。 たとえば、 `SSN` 列が暗号化されていると仮定して、パラメーター化せずに以下のクエリを正常に実行することはできません。   

```sql
DECLARE @SSN NCHAR(11) = '795-73-9838'
SELECT * FROM [dbo].[Patients]
WHERE [SSN] = @SSN
```

#### <a name="enablingdisabling-parameterization-for-always-encrypted"></a>Always Encrypted のパラメーター化の有効化/無効化

既定では、Always Encrypted のパラメーター化は無効になっています。

現在のクエリ エディター ウィンドウで Always Encrypted のパラメーター化を有効化/無効化するには、次のようにします。

1. メイン メニューから **[クエリ]** を選択します。
2. **[クエリ オプション...]** を選択します。
3. **[実行]**  >  **[詳細]** の順に移動します。
4. **[Always Encrypted のパラメーター化を有効にする]** を選択または選択解除します。
5. **[OK]** をクリックします。

今後のクエリ エディター ウィンドウで Always Encrypted のパラメーター化を有効化/無効化する場合は、次のようにします。

1. メイン メニューから **[ツール]** を選択します。
2. **[オプション...]** を選択します。
3. **[クエリ実行]**  >  **[SQL Server]**  >  **[詳細]** の順に移動します。
4. **[Always Encrypted のパラメーター化を有効にする]** を選択または選択解除します。
5. **[OK]** をクリックします。

Always Encrypted が有効な状態のデータベース接続を使用するクエリ エディター ウィンドウでクエリを実行する場合に、パラメーター化がクエリ エディター ウィンドウで有効になっていないと、有効にするよう求められます。

> [!NOTE]
> Always Encrypted のパラメーター化が機能するのは、Always Encrypted が有効な状態のデータベース接続を使用するクエリ エディター ウィンドウのみです (「 [データベース接続での Always Encrypted の有効化と無効化](#en-dis)」を参照)。 クエリ エディター ウィンドウで Always Encrypted が有効な状態ではないデータベース接続を使用すると、Transact-SQL 変数がパラメーター化されません。

#### <a name="how-parameterization-for-always-encrypted-works"></a>Always Encrypted のパラメーター化のしくみ

クエリ エディター ウィンドウでデータベース接続の Always Encrypted のパラメーター化と Always Encrypted の動作の両方が有効になっている場合、SQL Server Management Studio は、次の前提条件を満たす Transact-SQL 変数のパラメーター化を試みます。

- 同じステートメントで宣言され、初期化 (インライン初期化) されている。 別個の `SET` ステートメントを使用して宣言された変数はパラメーター化されません。
- 単一のリテラルを使用して初期化されている。 演算子または関数を含む式を使用して初期化された変数はパラメーター化されません。

SQL Server Management Studio がパラメーター化する、変数の例を以下に示します。

```sql
DECLARE @SSN char(11) = '795-73-9838';
   
DECLARE @BirthDate date = '19990104';
DECLARE @Salary money = $30000;
```

SQL Server Management Studio がパラメーター化を試みない変数の例を以下に示します。

```sql
DECLARE @Name nvarchar(50); --Initialization seperate from declaration
SET @Name = 'Abel';

DECLARE @StartDate date = GETDATE(); -- a function used instead of a literal

DECLARE @NewSalary money = @Salary * 1.1; -- an expression used instead of a literal
```
 
試行されたパラメーター化が正常に行われるようにするには   
- パラメーター化する変数の初期化で使用されるリテラルの型は、変数宣言の型と一致する必要があります。   
- 変数の宣言された型が date 型または time 型である場合、以下の ISO 8601 に準拠した形式のいずれかを使用する文字列で変数を初期化する必要があります。   

パラメーター化エラーの原因となる Transact-SQL 変数宣言の例を以下に示します。   
```sql
DECLARE @BirthDate date = '01/04/1999' -- unsupported date format   
   
DECLARE @Number int = 1.1 -- the type of the literal does not match the type of the variable   
```
SQL Server Management Studio では Intellisense を使用して、正常にパラメーター化できた変数と失敗したパラメーター化の試行 (およびその理由) を通知します。   

クエリ エディターでは、正常にパラメーター化できた変数の宣言に警告の下線が付けられます。 警告の下線が付いた宣言ステートメントにカーソルを置くと、パラメーター化プロセスの結果が表示されます。これには、結果の [SqlParameter](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.aspx) オブジェクト (変数に対応する) の次の主要なプロパティの値が含まれます:[SqlDbType](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sqldbtype.aspx)、[Size](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.size.aspx)、[Precision](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.precision.aspx)、[Scale](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.scale.aspx)、[SqlValue](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sqlvalue.aspx)。 また、 **[エラー一覧]** ビューの **[警告]** タブには、正常にパラメーター化されたすべての変数の完全な一覧も表示されます。 **[エラー一覧]** ビューを開くには、メイン メニューから **[ビュー]** を選択し、 **[エラー一覧]** を選択します。    

SQL Server Management Studio が変数のパラメーター化を試みたときに、パラメーター化が失敗した場合には、変数の宣言にエラーの下線が付けられます。 エラーの下線が付けられた宣言ステートメントにカーソルを置くと、エラーに関する結果が表示されます。 また、 **[エラー一覧]** ビューの **[エラー]** タブで、すべての変数のパラメーター化エラーの完全な一覧を表示することもできます。 **[エラー一覧]** ビューを開くには、メイン メニューから **[ビュー]** を選択し、 **[エラー一覧]** を選択します。   

下のスクリーン ショットは、6 つの変数宣言の例を示しています。 SQL Server Management Studio は、最初の 3 つの変数を正常にパラメーター化しています。 最後の 3 つの変数ではパラメーター化の前提条件が満たされなかったため、SQL Server Management Studio ではそれらのパラメーター化は試行されていません (宣言にはまったくマークが付けられていません)。

![always-encrypted-parameter-warnings](../../../relational-databases/security/encryption/media/always-encrypted-parameter-warnings.png)
 
次の別の例では、2 つの変数はパラメーター化の前提条件を満たしていますが、変数が正しく初期化されていないため、パラメーター化の試行は失敗しています。    
 
![always-encrypted-error](../../../relational-databases/security/encryption/media/always-encrypted-error.png)
 
> [!NOTE]
> Always Encrypted でサポートされる型変換のサブセットは限られているため、多くの場合、Transact-SQL 変数のデータ型が、ターゲットとなるターゲット データベース列の型と同じである必要があります。 たとえば、 `SSN` テーブル内の `Patients` 列の型が `char(11)`であると仮定して、 `@SSN` である、 `nchar(11)`変数の型が列の型と一致しないため、以下のクエリは失敗します。   

```sql
DECLARE @SSN nchar(11) = '795-73-9838'
SELECT * FROM [dbo].[Patients]
WHERE [SSN] = @SSN;
```

    Msg 402, Level 16, State 2, Line 5   
    The data types char(11) encrypted with (encryption_type = 'DETERMINISTIC', 
    encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'CEK_Auto1', 
    column_encryption_key_database_name = 'Clinic') collation_name = 'Latin1_General_BIN2' 
    and nchar(11) encrypted with (encryption_type = 'DETERMINISTIC', 
    encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'CEK_Auto1', 
    column_encryption_key_database_name = 'Clinic') are incompatible in the equal to operator.

> [!NOTE]
> パラメーター化しないと、型変換を含め、クエリ全体が SQL Server/Azure SQL Database 内で処理されます。 パラメーター化が有効になっている場合は、SQL Server Management Studio 内の .NET Framework でいくつかの型変換が実行されます。 .NET Framework 型システムと SQL Server 型システムには違いがある (float など、いくつかの型の精度が異なる) ため、パラメーター化を有効にして実行されたクエリでは、パラメーター化を有効にせずに実行されたクエリとは異なる結果が生成される場合があります。 

#### <a name="permissions-for-querying-against-encrypted-columns"></a>暗号化された列に対してクエリを実行するためのアクセス許可

暗号化テキストのデータを取得するクエリを含め、暗号化された列でクエリを実行するには、データベースでの `VIEW ANY COLUMN MASTER KEY DEFINITION` と `VIEW ANY COLUMN ENCRYPTION KEY DEFINITION` の権限が必要です。

これらの権限に加え、クエリ結果を暗号化解除する場合や、(Transact-SQL 変数をパラメーター化することで生成される) クエリ パラメーターを暗号化する場合には、ターゲット列を保護する列マスター キーにアクセスする必要もあります。

- **証明書ストア - ローカル コンピューター** 列マスター キーとして使用される証明書への `Read` アクセス権を持っているか、コンピューターの管理者である必要があります。   
- **Azure Key Vault** 列マスター キーが格納されている資格情報コンテナーに対する `get`、 `unwrapKey`、および verify の権限が必要です。
- **キー ストア プロバイダー (KSP)** キー ストアまたはキーを使用するときに入力を求められる可能性がある必要な権限と資格情報は、ストアと KSP の構成によって異なります。   
- **暗号化サービス プロバイダー (CSP)** キー ストアまたはキーを使用するときに入力を求められる可能性がある必要な権限と資格情報は、ストアと CSP の構成によって異なります。

詳細については、 [列マスター キーの作成と格納 (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md) を参照してください。

<a name="provisioncmk"></a>
## <a name="provisioning-column-master-keys-new-column-master-key"></a>列マスター キーのプロビジョニング (新しい列マスター キー)

**[新しい列マスター キー]** ダイアログでは、列マスター キーを生成することも、キー ストア内の既存のキーを選択することもできます。さらに、作成または選択したキーに対して列マスター キーのメタデータをデータベースに作成することができます。

1.  **オブジェクト エクスプローラー**を使用し、データベースの下の **[セキュリティ]、[Always Encrypted キー]** の順にアクセスします。
2.  **[列マスター キー]** フォルダーを右クリックし、 **[新しい列マスター キー...]** を選択します。 
3.  **[新しい列マスター キー]** ダイアログで、列マスター キーのメタデータ オブジェクトの名前を入力します。
4.  キー ストアを選択します。
    - **証明書ストア - 現在のユーザー** - Windows 証明書ストアでの現在のユーザーの証明書ストアの場所を示します。これは個人的なストアです。 
    - **証明書ストア - ローカル コンピューター** - Windows 証明書ストアでのローカル コンピューターの証明書ストアの場所を示します。 
    - **Azure Key Vault** - Azure にサインインする必要があります ( **[サインイン]** をクリックします)。 サインインすると、Azure サブスクリプションのいずれかとキー資格情報コンテナーを選択できるようになります。
    - **キー ストア プロバイダー (KSP)** - Cryptography Next Generation (CNG) API を実装するキー ストア プロバイダー (KSP) を介してアクセスできるキー ストアを示します。 通常、この種のストアは、ハードウェア セキュリティ モジュール (HSM) となります。 このオプションを選択したら、KSP を選択する必要があります。 既定では、**Microsoft ソフトウェア キー ストア プロバイダー** が選択されます。 HSM に格納されている列マスター キーを使用する場合は、デバイス用の KSP を選択します (ダイアログを開く前に、コンピューターにインストールし、構成しておく必要があります)。
    -   **暗号化サービス プロバイダー (CSP)** - 暗号化 API (CAPI) を実装する暗号化サービス プロバイダー (CSP) を介してアクセスできるキー ストアです。 通常、そのようなストアは、ハードウェア セキュリティ モジュール (HSM) です。 このオプションを選択したら、CSP を選択する必要があります。  HSM に格納されている列マスター キーを使用する場合は、デバイス用の CSP を選択します (ダイアログを開く前に、コンピューターにインストールし、構成しておく必要があります)。
    
    > [!NOTE]
    > CAPI は非推奨の API であるため、既定では暗号化サービス プロバイダー (CAPI) オプションは無効になります。 これを有効にするには、Windows レジストリの **[HKEY_CURRENT_USER\Software\Microsoft\Microsoft SQL Server\sql13\Tools\Client\Always Encrypted]** キーの下に CAPI Provider Enabled DWORD 値を作成し、これを 1 に設定します。 キー ストアで CNG がサポートされていない場合は、CAPI ではなく CNG を使用する必要があります。
   
    上記キー ストアの詳細については、 [Create and Store Column Master Keys (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)(列マスター キーの作成と格納 (Always Encrypted)) を参照してください。

5.  キー ストアにある既存のキーを選択するか、あるいは **[キーの生成]** ボタンまたは **[証明書の生成]** ボタンをクリックしてキー ストアにキーを作成します。 
6.  **[OK]** をクリックします。新しいキーが一覧に表示されます。 

SQL Server Management Studio により、データベースに列マスター キーのメタデータが作成されます。 ダイアログでこれを実現するには、 [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md) ステートメントを生成し発行します。


<a name="provisioncek"></a> 
## <a name="provisioning-column-encryption-keys-new-column-encryption-key"></a>列暗号化キーのプロビジョニング (新しい列暗号化キー)

**[新しい列の暗号化キー]** ダイアログでは、列暗号化キーを生成し、それを列マスター キーで暗号化し、データベースに列暗号化キーのメタデータを作成することができます。

1.  **オブジェクト エクスプローラー**を使用して、データベースの下にあるフォルダーを **[セキュリティ]、[Always Encrypted キー]** の順に移動します。
2.  **[列暗号化キー]** フォルダーを右クリックし、 **[新しい列の暗号化キー...]** を選択します。 
3.  **[新しい列の暗号化キー]** ダイアログで、列暗号化キーのメタデータ オブジェクトの名前を入力します。
4.  データベースの列マスター キーを表すメタデータ オブジェクトを選択します。
5.  **[OK]** をクリックします。 


SQL Server Management Studio では、新しい列暗号化キーを生成し、選択した列マスター キーのメタデータをデータベースから取得します。 次に SQL Server Management Studio は、列マスター キーのメタデータを使用することで、該当する列マスター キーを含むキー ストアと交信して、列暗号化キーを暗号化します。 最後に、新しい列暗号化キーのメタデータがデータベースに作成されます。 ダイアログでこれを実現するには、 [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/create-column-encryption-key-transact-sql.md) ステートメントを生成し発行します。

### <a name="permissions-for-provisioning-a-column-encryption-key"></a>列暗号化キーをプロビジョニングするためのアクセス許可

ダイアログで、列暗号化キーのメタデータを作成し、列マスター キーのメタデータにアクセスするには、 *ALTER ANY ENCRYPTION MASTER KEY* および *VIEW ANY COLUMN MASTER KEY DEFINITION* データベース権限が必要です。
キー ストアにアクセスして、列マスター キーを使用するには、キー ストアとキーの両方、またはそのいずれかに対する権限が必要な場合があります。
- **証明書ストア - ローカル コンピューター** - 列マスター キーとして使用される証明書への読み取りアクセス権を持っているか、コンピューターの管理者である必要があります。
- **Azure Key Vault** - 列マスター キーが格納されている資格情報コンテナーに対して *get*、*unwrapKey*、*wrapKey*、*sign*、および *verify* の権限が必要です。
- **キー ストア プロバイダー (CNG)** - キー ストアまたはキーを使用する際には、ストアと KSP の構成に応じて、必要な権限と資格情報を入力するよう求められる場合があります。
- **暗号化サービス プロバイダー (CAPI)** - キー ストアまたはキーを使用する際には、ストアと CSP の構成に応じて、必要な権限と資格情報を入力するよう求められる場合があります。

詳細については、 [列マスター キーの作成と格納 (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md) を参照してください。

<a name="rotatecmk"></a>
## <a name="rotating-column-master-keys"></a>列マスター キーの回転

列マスター キーの回転は、既存の列マスター キーを新しい列マスター キーに置き換える処理です。 キーの回転は、キーが侵害されている場合に、または必須の暗号化キーを定期的に回転することを求めた組織のポリシーまたはコンプライアンス規定に準拠するために、行うことが必要な場合があります。 列マスター キーの回転では、現在の列マスター キーで保護された列暗号化キーを暗号化解除し、新しい列マスター キーを使用して列暗号化キーを再度暗号化し、キーのメタデータを更新するという処理が必要です。 詳細については、「 [Overview of Key Management for Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)(Always Encrypted のキー管理の概要)」を参照してください。

**ステップ 1:新しい列マスター キーをプロビジョニングする**

前述の「列マスター キーのプロビジョニング」セクションの手順に従って、新しい列マスター キーをプロビジョニングします。

**ステップ 2:新しい列マスター キーで列暗号化キーを暗号化する**

列マスター キーは、通常、1 つまたは複数の列暗号化キーを保護します。 列暗号化キーを列マスター キーにより暗号化すると、各列暗号化キーの暗号化された値がデータベースに格納されます。
この手順では、回転する列マスター キーで保護されている各列暗号化キーを新しい列マスター キーで暗号化し、新しい暗号化された値をデータベースに格納します。 結果的に、回転の影響を受けた各列暗号化キーには暗号化された値が 2 つ含まれることになります。1 つは既存の列マスター キーにより暗号化された値、もう 1 つは新しい列マスター キーで暗号化された値です。

1.  **オブジェクト エクスプローラー**で **[セキュリティ] > [Always Encrypted キー] > [列マスター キー]** フォルダーの順に移動し、回転する列マスター キーを探します。
2.  列マスター キーを右クリックし、 **[回転]** を選択します。
3.  **[列マスター キーの回転]** ダイアログの **[ターゲット]** フィールドで、手順 1 で作成した、新しい列マスター キーの名前を選択します。
4.  既存の列マスター キーで保護された、列暗号化キーの一覧を確認します。 これらのキーは、回転の影響を受けます。
5.  **[OK]** をクリックします。

SQL Server Management Studio では、古い列マスター キーで保護された列暗号化キーのメタデータと、古い列マスター キーおよび新しい列マスター キーのメタデータを取得します。 次に、SSMS では、列マスター キーのメタデータを使用することで、古い列マスター キーが格納されたキー ストアにアクセスし、列暗号化キーを暗号化解除します。 さらに、SSMS では、新しい列マスター キーを保持しているキー ストアにアクセスして、列暗号化キーの暗号化された値セットを新たに作成し、その新しい値をメタデータに追加します ( [ALTER COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/alter-column-encryption-key-transact-sql.md) ステートメントの生成および発行)。

> [!NOTE]
> 古い列マスター キーで暗号化されたそれぞれの列暗号化キーが他の列マスター キーで暗号化されていないことを確認します。 つまり、回転の影響を受けるすべての列暗号化キーに、データベースの暗号化された値が 1 つだけ含まれている必要があります。 影響を受ける列暗号化キーのいずれかに複数の暗号化された値が含まれている場合、回転を続行する前にその値を削除する必要があります (列暗号化キーの暗号化された値を削除する方法は、 *"手順 4"* を参照してください)。

**ステップ 3:新しい列マスター キーでアプリケーションを構成する**

この手順では、回転している列マスター キーで保護されたデータベース列 (つまり、回転されている列マスター キーで暗号化される列暗号化キーで暗号化されたデータベース列) に対してクエリを実行するすべてのクライアント アプリケーションが、新しい列マスター キーにアクセスできるようにする必要があります。 この手順は、新しい列マスター キーが格納されているキー ストアの種類によって異なります。 例:

- 新しい列マスター キーが Windows 証明書ストアに格納された証明書である場合、データベースの列マスター キーのキー パスに指定された場所と同じ証明書ストアの場所 ( *[現在のユーザー]* または *[ローカル コンピューター]* ) に証明書を展開する必要があります。 アプリケーションが、証明書にアクセスできる必要があります。
  - 証明書が、"*現在のユーザー*" の証明書ストアに格納されている場合、証明書をアプリケーションの Windows ID (ユーザー) の [現在のユーザー] ストアにインポートする必要があります。
  - 証明書が "*ローカル コンピューター*" の証明書ストアに格納されている場合、アプリケーションの Windows ID に証明書へのアクセス許可が必要です。
- 新しい列マスター キーが Microsoft Azure Key Vault に格納されている場合は、アプリケーションが Azure を認証でき、キーにアクセスできるように実装する必要があります。

詳細については、「 [Create and Store Column Master Keys (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)(列マスター キーの作成と格納 (Always Encrypted))」を参照してください。

> [!NOTE]
> 回転のこの時点では、古い列マスター キーと新しい列マスター キーの両方が有効であり、これらを使ってデータにアクセスすることができます。

**ステップ 4:古い列マスター キーで暗号化された列暗号化キーの値をクリーンアップする**

新しい列マスター キーを使用するようにすべてのアプリケーションを構成したら、 *"古い"* 列マスター キーで暗号化された列暗号化キーの値をデータベースから削除します。新しい列マスター キーを使用するようにすべてのアプリケーションを構成したら、古い列マスター キーで暗号化された列暗号化キーの値をデータベースから削除します。 古い値を削除することで、次の回転を行うことができます (ただし、回転される列マスター キーで保護されたすべての列暗号化キーに、必ず暗号化された値が 1 つ必要です)。

古い列マスター キーをアーカイブまたは削除する前に古い値をクリーンアップするもう 1 つの理由は、パフォーマンスに関係します。暗号化された列にクエリを実行すると、Always Encrypted が有効なクライアント ドライバーで、古い値と新しい値の 2 つの暗号化を解除しなければならない場合があるからです。 ドライバーでは、アプリケーションの環境で 2 つの列マスター キーのどちらが有効かは認識されません。このため、ドライバーでは暗号化された値が両方ともサーバーから取得されます。 使用できない列マスター キー (ストアから削除されている古い列マスター キーなど) で暗号化されていることにより一方の値の暗号化の解除が失敗すると、ドライバーでは新しい列マスター キーを使用してもう一方の値の暗号化の解除が試みられます。

> [!WARNING]
> 対応する列マスター キーがアプリケーションで使用できるようになる前に列暗号化キーの値を削除すると、データベース列をアプリケーションが暗号化解除できなくなります。

1.  **オブジェクト エクスプローラー**で、 **[セキュリティ]、[Always Encrypted キー]** フォルダーの順に移動し、交換する既存の列マスター キーを探します。
2.  既存の列マスター キーを右クリックし、 **[クリーンアップ]** を選択します。
3.  削除される列暗号化キーの値の一覧を確認します。
4.  **[OK]** をクリックします。

SQL Server Management Studio では、 [ALTER COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/alter-column-encryption-key-transact-sql.md) ステートメントを発行して、古い列マスター キーで暗号化された列暗号化キーの暗号化された値を削除します。

**ステップ 5:古い列マスター キーのメタデータを削除する**

データベースから古い列マスター キーの定義を削除する場合は、次の手順を使用します。

1. **オブジェクト エクスプローラー**で **[セキュリティ]、[Always Encrypted キー]、[列マスター キー]** フォルダーの順に移動し、データベースから削除する古い列マスター キーを探します。
2. 古い列マスター キーを右クリックし、 **[削除]** を選択します ( [DROP COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/drop-column-master-key-transact-sql.md) ステートメントが生成および発行され、列マスター キーのメタデータが削除されます)。
3. **[OK]** をクリックします。

> [!NOTE]
> 回転の後、古い列マスター キーは完全に削除しないを強くお勧めします。 そこで、古い列マスター キーを現在のキー ストアに保存するか、セキュリティで保護された別の場所にアーカイブします。 バックアップ ファイルからデータベースを復元して、新しい列マスター キーを構成する前の時点まで戻る場合は、古いキーでデータにアクセスする必要があります。

### <a name="permissions-for-rotating-column-master-key"></a>列マスター キーを回転するためのアクセス許可

列マスター キーを回転するには、次のデータベース権限が必要です。

- **ALTER ANY COLUMN MASTER KEY** - 新しい列マスター キーのメタデータを作成し、古い列マスター キーのメタデータを削除するのに必要です。
- **ALTER ANY COLUMN ENCRYPTION KEY** - 列暗号化キーのメタデータを変更するのに必要です (新しい暗号化された値の追加)。
- **VIEW ANY COLUMN MASTER KEY DEFINITION** - 列マスター キーのメタデータにアクセスして読み取るのに必要です。
- **VIEW ANY COLUMN ENCRYPTION KEY DEFINITION** - 列暗号化キーの列メタデータにアクセスして読み取るのに必要です。 

また、キー ストアにある古い列マスター キーと新しい列マスター キーの両方にアクセスできることも必要です。 キー ストアにアクセスして、列マスター キーを使用するには、キー ストアとキーの両方、またはそのいずれかに対する権限が必要な場合があります。
- **証明書ストア – ローカル コンピューター** - 列マスター キーとして使用される証明書への読み取りアクセス権を持っているか、コンピューターの管理者である必要があります。
- **Azure Key Vault** - 列マスター キーが格納されている資格情報コンテナーに対する *create*、*get*、*unwrapKey*、*wrapKey*、*sign*、および *verify* 権限が必要です。
- **キー ストア プロバイダー (CNG)** - キー ストアまたはキーを使用する際には、ストアと KSP の構成に応じて、必要な権限と資格情報を入力するよう求められる場合があります。
- **暗号化サービス プロバイダー (CAPI)** - キー ストアまたはキーを使用する際には、ストアと CSP の構成に応じて、必要な権限と資格情報を入力するよう求められる場合があります。

詳細については、 [列マスター キーの作成と格納 (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md) を参照してください。

<a name="rotatecek"></a> 
## <a name="rotating-column-encryption-keys"></a>列暗号化キーの回転

列暗号化キーを回転するには、回転するキーで暗号化されたすべての列のデータを暗号化解除し、新しい列暗号化キーを使用してデータを再度暗号化する必要があります。

>[!NOTE]
> 回転するキーで暗号化された列を含むテーブルが大きい場合、列暗号化キーの回転には長い時間がかかることがあります。 データが再暗号化されている間、アプリケーションは影響を受けるテーブルへの書き込みを行うことができません。 したがって、組織で列暗号化キーを回転する場合は、慎重に計画を立てる必要があります。
列暗号化キーを回転するには、Always Encrypted ウィザードを使用します。

1.  データベースのウィザードを開きます。それには、データベースを右クリックして **[タスク]** をポイントし、 **[列の暗号化]** をクリックします。
2.  **[概要]** ページの内容を確認し、 **[次へ]** をクリックします。
3.  **[列の選択]** ページで、テーブルを展開し、古い列暗号化キーで現在暗号化されている列で、置換する列をすべて特定します。
4.  古い列暗号化キーで暗号化されたそれぞれの列について、 **[暗号化キー]** を新しい自動生成キーに設定します。 **注:** あるいは、ウィザードを実行する前に、新しい列暗号化キーを作成しておくこともできます。前述の「*列暗号化キーのプロビジョニング*」セクションを参照してください。
5.  **[マスター キーの構成]** ページで、新しいキーを格納する場所を選択し、マスター キー ソースを選択し、 **[次へ]** をクリックします。 **注:** 既存の列暗号化キーを使用する (自動生成されたものではなく) 場合、このページで実行するアクションはありません。
6.  **[検証]** ページで、スクリプトをすぐに実行するか PowerShell スクリプトを作成するかを選択し、 **[次へ]** をクリックします。
7.  **[概要]** ページで、選択したオプションを確認し、完了したら **[完了]** をクリックしてウィザードを閉じます。
8.  **オブジェクト エクスプローラー**で **[セキュリティ]、[Always Encrypted キー]、[列暗号化キー]** フォルダーの順に移動し、データベースから削除する古い列暗号化キーを探します。 キーを右クリックし、 **[削除]** をクリックします。

### <a name="permissions-for-rotating-column-encryption-keys"></a>列暗号化キーを回転するためのアクセス許可

列暗号化キーを回転するために必要なデータベース権限:**ALTER ANY COLUMN MASTER KEY** - 新しい自動生成の列暗号化キーを使用する場合に必要です (新しい列マスター キーとその新しいメタデータも生成されます)。
**ALTER ANY COLUMN ENCRYPTION KEY** - 新しい列暗号化キーのメタデータを追加するのに必要です。
**VIEW ANY COLUMN MASTER KEY DEFINITION** - 列マスター キーのメタデータにアクセスして読み取るのに必要です。
**VIEW ANY COLUMN ENCRYPTION KEY DEFINITION** - 列暗号化キーの列メタデータにアクセスして読み取るのに必要です。

また、新しい列暗号化キーと古い列暗号化キーの両方の列マスター キーにアクセスできることも必要です。 キー ストアにアクセスして、列マスター キーを使用するには、キー ストアとキーの両方、またはそのいずれかに対する権限が必要な場合があります。
- **証明書ストア – ローカル コンピューター** - 列マスター キーとして使用される証明書への読み取りアクセス権を持っているか、コンピューターの管理者である必要があります。
- **Azure Key Vault** - 列マスター キーが格納されている資格情報コンテナーに対する get、unwrapKey、および verify の権限が必要です。
- **キー ストア プロバイダー (CNG)** - キー ストアまたはキーを使用する際には、ストアと KSP の構成に応じて、必要な権限と資格情報を入力するよう求められる場合があります。
- **暗号化サービス プロバイダー (CAPI)** - キー ストアまたはキーを使用する際には、ストアと CSP の構成に応じて、必要な権限と資格情報を入力するよう求められる場合があります。

詳細については、 [列マスター キーの作成と格納 (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md) を参照してください。

## <a name="performing-dac-upgrade-operations-when-database-or-dacpac-uses-always-encrypted"></a>データベースまたは DACPAC で Always Encrypted が使用されている場合に DAC アップグレード操作を実行する

[DAC 操作](../../data-tier-applications/data-tier-applications.md) は、暗号化された列がスキーマに含まれている DACPAC ファイルとデータベースに対してサポートされています。 DAC のアップグレード操作には、特別な考慮事項が適用されます。SSMS など、さまざまなツールで DAC のアップグレード操作を実行する方法については、「[データ層アプリケーションのアップグレード](../../../relational-databases/data-tier-applications/upgrade-a-data-tier-application.md)」を参照してください。 

DACPAC を使用してデータベースをアップグレードする場合、DACPAC またはターゲット データベースのいずれかに暗号化された列が含まれていると、次の条件がすべて満たされた場合に、アップグレード操作によってデータの暗号化操作をトリガーします。
- データベースにデータを含む列が含まれています。
- DACPAC にも同じ列が存在します。
- データベース内の列の暗号化の構成が、DACPAC 内の対応する列の構成と異なります。 詳細については、次の表を参照してください。

| 条件|操作|
|:---|:---|
|列は、DACPAC では暗号化され、データベースでは暗号化されていません。| 列のデータは暗号化されます。|
|列は、DACPAC では暗号化されておらず、データベースでは暗号化されています。| 列のデータは暗号化解除されます (列の暗号化は解除されます)。|
| DACPAC とデータベースの両方で列は暗号化されていますが、DACPAC の列で使用される暗号化の種類および/または列暗号化キーは、データベースの対応する列の場合と異なっています。|列のデータは暗号化解除され、DACPAC の暗号化の構成に一致するように再び暗号化されます。|

> [!NOTE]
> データベースまたは DACPAC の列に対して構成された列マスター キーが Azure Key Vault に格納されている場合は、Azure にサインインするように求められます (まだサインインしていない場合)。

### <a name="permissions-for-dac-upgrade-if-always-encrypted-is-set-up"></a>Always Encrypted が設定されている場合に DAC をアップグレードするためのアクセス許可

DACPAC またはターゲット データベースで Always Encrypted がセットアップされている場合に DAC アップグレード操作を実行するには、DACPAC 内のスキーマとターゲット データベースのスキーマとの違いに応じて、次に示す権限の一部またはすべてが必要な場合があります。

*ALTER ANY COLUMN MASTER KEY*、 *ALTER ANY COLUMN ENCRYPTION KEY*、 *VIEW ANY COLUMN MASTER KEY DEFINITION*、 *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION*

アップグレード操作によってデータ暗号化操作がトリガーされる場合、影響を受ける列に対して構成された列マスター キーにアクセスできることも必要です。

- **証明書ストア – ローカル コンピューター** - 列マスター キーとして使用される証明書への読み取りアクセス権を持っているか、コンピューターの管理者である必要があります。
- **Azure Key Vault** - 列マスター キーが格納されている資格情報コンテナーに対する *create*、*get*、*unwrapKey*、*wrapKey*、*sign*、および *verify* 権限が必要です。
- **キー ストア プロバイダー (CNG)** - キー ストアまたはキーを使用する際には、ストアと KSP の構成に応じて、必要な権限と資格情報を入力するよう求められる場合があります。
- **暗号化サービス プロバイダー (CAPI)** - キー ストアまたはキーを使用する際には、ストアと CSP の構成に応じて、必要な権限と資格情報を入力するよう求められる場合があります。

詳細については、 [列マスター キーの作成と格納 (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md) を参照してください。

## <a name="migrating-databases-with-encrypted-columns-using-bacpac"></a>暗号化された列を含むデータベースを BACPAC を使用して移行する

データベースをエクスポートすると、暗号化された列に格納されているすべてのデータが取得され、結果として生成された [BACPAC](../../data-tier-applications/data-tier-applications.md) に入れられます (暗号化された形式で)。 生成された BACPAC には、Always Encrypted キーのメタデータも含まれます。

BACPAC をデータベースにインポートすると、BACPAC からの暗号化されたデータがデータベースに読み込まれ、Always Encrypted キーのメタデータが再び作成されます。

ソース データベース (エクスポートしたデータベース) に格納されている暗号化されたデータを変更または取得するように構成されたアプリケーションがある場合、特別なことをしなくても、そのアプリケーションでターゲット データベース内の暗号化されたデータに対してクエリを実行することができます。これは両方のデータベースのキーが同じであるためです。

### <a name="permissions-for-migrating-databases-with-encrypted-columns"></a>暗号化された列を含むデータベースを移行するためのアクセス許可

ソース データベースに対して *ALTER ANY COLUMN MASTER KEY* および *ALTER ANY COLUMN ENCRYPTION KEY* 権限が必要です。 ターゲット データベースに対して *ALTER ANY COLUMN MASTER KEY*、 *ALTER ANY COLUMN ENCRYPTION KEY*、 *VIEW ANY COLUMN MASTER KEY DEFINITION*、および *VIEW ANY COLUMN ENCRYPTION* 権限が必要です。

## <a name="migrating-databases-with-encrypted-columns-using-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードを使用して暗号化された列を含むデータベースを移行する

[SQL Server インポートおよびエクスポート ウィザード](~/integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md) を使用すると、BACPAC ファイルの場合に比べて、暗号化された列に格納されたデータをデータ移行中に処理する方法をより詳細に制御することができます。

- データ ソースが Always Encrypted を使用したデータベースである場合は、データ ソース接続を構成して、エクスポート操作中に、暗号化された列に格納されたデータが暗号化解除されるようにすることも、暗号化されたまま維持されるようにすることもできます。
- データ ターゲットが Always Encrypted を使用したデータベースである場合は、暗号化された列をターゲットとするデータが暗号化解除されるようにデータ ターゲット接続を構成することができます。

暗号化解除 (データ ソースの場合) または暗号化 (データ ターゲットの場合) を有効にするには、 [.Net Framework Data Provider for SqlServer](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) を使用するようにデータ ソース/ターゲットを構成する必要があるほか、Column Encryption Setting 接続文字キーワードを *Enabled*に設定する必要があります。

次の表では、考えられる移行シナリオを示し、さらに、これらのシナリオが Always Encrypted と共にデータ ソースとデータ ターゲットの接続構成にどのように関係するのかを説明します。

| シナリオ|ソース接続構成| ターゲット接続構成
|:---|:---|:---
|移行時にデータを暗号化する (データはデータ ソースにプレーンテキストとして保存されており、データ ターゲットの暗号化された列に移行されます)。| データ プロバイダー/ドライバー: *"任意"*<br><br>Column Encryption Setting = Disabled<br><br>(.Net Framework Data Provider for SqlServer および .NET Framework 4.6 以降が使用される場合) | データ プロバイダー/ドライバー: *.Net Framework Data Provider for SqlServer* (.NET Framework 4.6 以降が必要)<br><br>Column Encryption Setting = Enabled
| 移行時にデータを暗号化解除する (データは、データ ソースの暗号化された列に格納されており、プレーンテキストの形式でデータ ターゲットに移行されます。データ ターゲットがデータベースである場合、ターゲット列は暗号化されません)。<br><br>**注:** 暗号化された列を含むターゲット テーブルは、移行の前に存在する必要があります。|データ プロバイダー/ドライバー: *.Net Framework Data Provider for SqlServer* (.NET Framework 4.6 以降が必要)<br><br>[追加のプロパティ]|データ プロバイダー/ドライバー: *"任意"*<br><br>Column Encryption Setting = Disabled<br><br>(.Net Framework Data Provider for SqlServer および .NET Framework 4.6 以降が使用される場合)
|移行時にデータを再暗号化する (データは、データ ソースの暗号化された列に格納されており、プレーンテキストの形式でデータ ターゲットに移行され、別種の暗号化の列暗号化キーを使用する列に格納されます)。<br><br>**注:** 暗号化された列を含むターゲット テーブルは、移行の前に存在する必要があります。| データ プロバイダー/ドライバー: *.Net Framework Data Provider for SqlServer* (.NET Framework 4.6 以降が必要)<br><br>[追加のプロパティ]|データ プロバイダー/ドライバー: *.Net Framework Data Provider for SqlServer* (.NET Framework 4.6 以降が必要)<br><br>[追加のプロパティ]
|暗号化を解除することなく、暗号化されたデータを移動します。<br><br>**注:** 暗号化された列を含むターゲット テーブルは、移行の前に存在する必要があります。| データ プロバイダー/ドライバー: *"任意"*<br>Column Encryption Setting = Disabled<br><br>(.Net Framework Data Provider for SqlServer および .NET Framework 4.6 以降が使用される場合)| データ プロバイダー/ドライバー: *"任意"*<br>Column Encryption Setting = Disabled<br><br>(.Net Framework Data Provider for SqlServer および .NET Framework 4.6 以降が使用される場合)<br><br>ユーザーは、ALLOW_ENCRYPTED_VALUE_MODIFICATIONS を ON に設定する必要があります。<br><br>詳細については、 [Always Encrypted で保護された機微なデータの移行](../../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md)を参照してください。

### <a name="permissions-for-database-migration-using-sql-server-import-and-export-wizard"></a>SQL Server インポートおよびエクスポート ウィザードを使用してデータベースを移行するためのアクセス許可

データ ソースに格納されたデータを **暗号化** または **暗号化解除** するには、ソース データベースの *VIEW ANY COLUMN MASTER KEY DEFINITION* および *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* 権限が必要です。

暗号化または暗号化解除するデータを格納する列に対して構成された列マスター キーへのアクセス権も必要です。

- **証明書ストア – ローカル コンピューター** - 列マスター キーとして使用される証明書への読み取りアクセス権を持っているか、コンピューターの管理者である必要があります。
- **Azure Key Vault** - 列マスター キーが格納されている資格情報コンテナーに対して get、unwrapKey、wrapKey、sign、および verify の権限が必要です。
- **キー ストア プロバイダー (CNG)** - キー ストアまたはキーを使用する際に入力を求められる可能性がある必要な権限と資格情報は、ストアと KSP の構成によって異なります。
- **暗号化サービス プロバイダー (CAPI)** - キー ストアまたはキーを使用する際に入力を求められる可能性がある必要な権限と資格情報は、ストアと CSP の構成によって異なります。
詳細については、 [列マスター キーの作成と格納 (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md) を参照してください。

## <a name="see-also"></a>参照
- [Always Encrypted (データベース エンジン)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Always Encrypted ウィザード](../../../relational-databases/security/encryption/always-encrypted-wizard.md)
- [Always Encrypted のキー管理の概要](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [列マスター キーを作成して保存する (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)
- [Always Encrypted (クライアント開発)](../../../relational-databases/security/encryption/always-encrypted-client-development.md)
- [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md)
- [DROP COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/drop-column-master-key-transact-sql.md)
- [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/create-column-encryption-key-transact-sql.md)
- [ALTER COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/alter-column-encryption-key-transact-sql.md)
- [DROP COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/drop-column-encryption-key-transact-sql.md) 
- [sys.column_master_keys (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
- [sys.column_encryption_keys (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)
- [PowerShell を使用した Always Encrypted の構成](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)