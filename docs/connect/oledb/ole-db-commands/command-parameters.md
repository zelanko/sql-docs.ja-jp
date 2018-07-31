---
title: コマンド パラメーター | Microsoft Docs
description: コマンド パラメーター
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- parameters [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, parameters
- OLE DB Driver for SQL Server, commands
- parameters [OLE DB Driver for SQL Server], OLE DB
- commands [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 9b4e12d36c00769be83e01e47fafbd2e18421aa1
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106428"
---
# <a name="command-parameters"></a>コマンド パラメーター
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  コマンド テキスト内のパラメーターは、疑問符文字でマークされます。 たとえば、次の SQL ステートメントでは 1 つの入力パラメーターがマークされています。  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 ネットワーク トラフィックを削減してパフォーマンスを向上するために、OLE DB Driver for SQL Server では、コマンドの実行前に **ICommandWithParameters::GetParameterInfo** または **ICommandPrepare::Prepare** が呼び出されない限り、パラメーター情報の自動抽出は行いません。 つまり、OLE DB Driver for SQL Server が自動的にしません。  
  
-   **ICommandWithParameters::SetParameterInfo** で指定されたデータ型の正当性を確認すること。  
  
-   アクセサー バインド情報で指定された DBTYPE から、そのパラメーターに対する適切な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型にマップすること。  
  
 アプリケーションで [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型のパラメーターと互換性のないデータ型を指定すると、上記のいずれかが原因で、エラーが発生したり、有効桁数が失われる可能性があります。  
  
 このようなことが起きないようにするには、アプリケーションで次の条件を満たす必要があります。  
  
-   **ICommandWithParameters::SetParameterInfo** をハードコーディングしている場合、*pwszDataSourceType* をパラメーターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型と一致させます。  
  
-   アクセサーをハードコーディングしている場合、パラメーターにバインドされている DBTYPE 値の型を、パラメーターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型と同じにします。  
  
-   **ICommandWithParameters::GetParameterInfo** を呼び出すようにアプリケーションをコーディングし、プロバイダーでパラメーターの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型を動的に取得できるようにします。 これにより、ネットワーク上でサーバーとの余分なやり取りが増えることに注意してください。  
  
> [!NOTE]  
>  SQL Native Client OLE DB プロバイダーでは、FROM 句が含まれている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UPDATE ステートメントや DELETE ステートメント、パラメーターを含むサブクエリに依存する SQL ステートメント、比較の両方の式、LIKE 述部、および定量化された述語内にパラメーター マーカーを含む SQL ステートメント、またはパラメーターのいずれかが、関数に対するパラメーターになっているクエリの場合は、**ICommandWithParameters::GetParameterInfo** を呼び出すことはできません。 また、SQL ステートメントをバッチ処理する場合、バッチ内の最初のステートメントの後にあるステートメント内のパラメーター マーカーに対して、**ICommandWithParameters::GetParameterInfo** を呼び出すことはできません。 [!INCLUDE[tsql](../../../includes/tsql-md.md)] コマンド内ではコメント (/* \*/) を使用できません。  
  
 OLE DB Driver for SQL Server では、SQL ステートメント コマンドの入力パラメーターをサポートします。 プロシージャ呼び出しコマンドで、OLE DB Driver for SQL Server には、入力、出力、および入力/出力パラメーターがサポートしています。 出力パラメーターの値は、実行時 (行セットが返されない場合のみ)、または返されたすべての行セットがアプリケーションによって使用されたときにアプリケーションに返されます。 返される値が有効であることを保証するには、**IMultipleResults** を使用して行セットを強制的に使用します。  
  
 ストアド プロシージャ パラメーターの名前を DBPARAMBINDINFO 構造体で指定する必要はありません。 OLE DB Driver for SQL Server でパラメーター名を無視し、**ICommandWithParameters::SetParameterInfo** の *rgParamOrdinals* メンバーで指定された序数だけを使用する必要があることを示すには、*pwszName* メンバーの値に NULL を使用します。 コマンド テキストに名前付きのパラメーターと名前のないパラメーターの両方が含まれている場合、どの名前付きパラメーターよりも前に、名前のないパラメーターをすべて指定する必要があります。  
  
 ストアド プロシージャ パラメーターの名前が指定された場合、OLE DB Driver for SQL Server ではその名前が妥当かどうかがチェックされます。 OLE DB Driver for SQL Server は、コンシューマーから不適切なパラメーター名を受信すると、エラーを返します。  
  
> [!NOTE]  
>  OLE DB Driver for SQL Server には [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML と UDT (ユーザー定義型) のサポートを公開するために、新しい [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md) インターフェイスが実装されています。  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../oledb/ole-db-commands/commands.md)  
  
  
