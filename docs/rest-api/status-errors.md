---
id: status-errors
title: Status Errors
---
This section describes the error messages that can be returned via status channel after announcing a transaction.

<div class="info">

**Note:**

Configuration parameters are [editable](https://github.com/proximax-storage/cpp-xpx-chain/blob/master/resources/config-network.properties). Public network configuration may differ.

</div>

|**Status** |	**Description**|
|-------------|---------------------|
| Success | Validation result is success.|
| Neutral	| Validation result is neither success nor failure.|
| Failure | Validation result is failure.|
| Failure_Core_Past_Deadline | Validation failed because the deadline passed.|
| Failure_Core_Future_Deadline | Validation failed because the deadline is too far in the future. Deadlines are only allowed to lie up to `24` hours ahead. |
| Failure_Core_Insufficient_Balance |	Validation failed because the account has an insufficient balance. |
| Failure_Core_Too_Many_Transactions | Validation failed because there are too many transactions in a block. |
| Failure_Core_Nemesis_Account_Signed_After_Nemesis_Block | Validation failed because an entity originated from the nemesis account after the nemesis block. |
| Failure_Core_Wrong_Network | Validation failed because the entity has the wrong network specified. |
| Failure_Core_Invalid_Address | Validation failed because an address is invalid. |
| Failure_Core_Invalid_Version | Validation failed because the version of a block or a tranaction is invalid. |
| Failure_Core_Invalid_Transaction_Fee | Validation failed because the transaction fee is invalid. |
| Failure_Core_Block_Harvester_Ineligible | Validation failed because a block was validated by an ineligible validator. |
| Failure_Core_Invalid_FeeInterest | Validation failed because the fee interest coefficient is invalid. |
| Failure_Core_Invalid_FeeInterestDenominator | Validation failed because the denominator of fee interest coefficient is invalid. |
| Failure_Hash_Exists | Validation failed because the entity hash is already known. |
| Failure_Signature_Not_Verifiable | Validation failed because the verification of the signature failed. |
| Failure_AccountLink_Invalid_Action 	| Validation failed because the account link action is invalid: link (0) and unlink (1). |
| Failure_AccountLink_Link_Already_Exists |	Validation failed because the main account is already linked to another account. |
| Failure_AccountLink_Link_Does_Not_Exist |	Validation failed because the unlink data is not consistent with existing account link. |
| Failure_AccountLink_Unlink_Data_Inconsistency |	Validation failed because the unlink data is not consistent with existing account link. |
| Failure_AccountLink_Remote_Account_Ineligible |	Validation failed because the link is attempting to convert ineligible account to remote. |
| Failure_AccountLink_Remote_Account_Signer_Not_Allowed |	Validation failed because the remote is not allowed to sign a transaction. |
| Failure_AccountLink_Remote_Account_Participant_Not_Allowed |	Validation failed because the remote is not allowed to participate in the  transaction. |
| Failure_Aggregate_Too_Many_Transactions |	Validation failed because an aggregate has too many transactions. An aggregate transaction can contain up to `1000` inner transactions. |
| Failure_Aggregate_No_Transactions |	Validation failed because an aggregate does not have any transactions. |
| Failure_Aggregate_Too_Many_Cosignatures |	Validation failed because an aggregate has too many cosignatures. The maximum number of cosignatories allowed is `15`. |
| Failure_Aggregate_Redundant_Cosignatures |	Validation failed because there are redundant cosignatures. |
| Failure_Aggregate_Ineligible_Cosigners |	Validation failed because at least one cosigner is ineligible. |
| Failure_Aggregate_Missing_Cosigners |	Validation failed because at least one required cosigner is missing. The tranaction was announced as complete but had missing cosignatures. |
| Failure_Aggregate_Plugin_Config_Malformed |	Validation failed because the aggregate transaction plugin configuration is malformed. |
| Failure_Aggregate_Bonded_Not_Enabled |	Validation failed because aggregate bonded tranaction is not enabled. |
| Failure_NetworkConfig_Invalid_Signer | Validation failed because the transaction signer is not nemesis account. |
| Failure_NetworkConfig_BlockChain_Config_Too_Large | Validation failed because the network configuration size exceeded the limit. |
| Failure_NetworkConfig_Config_Redundant | Validation failed because a network configuration has already been set up at the height. |
| Failure_NetworkConfig_BlockChain_Config_Malformed | Validation failed because the network configuration is malformed. |
| Failure_NetworkConfig_Plugin_Config_Malformed | Validation failed because the configuration of network configuration plugin is malformed. |
| Failure_NetworkConfig_SupportedEntityVersions_Config_Too_Large | Validation failed because the supported entity configuration exceeded the limit. |
| Failure_NetworkConfig_SupportedEntityVersions_Config_Malformed | Validation failed because the supported entity configuration is malformed. |
| Failure_NetworkConfig_Catapult_Config_Trx_Cannot_Be_Unsupported | Validation failed because the supported entity versions configuration has no version of the network config transaction. |
|Failure_NetworkConfig_Plugin_Config_Missing | Validation failed because some plugin config missing. |
|Failure_NetworkConfig_ImportanceGrouping_Less_Or_Equal_Half_MaxRollbackBlocks | Validation failed because of the block less or equal half max rollback blocks. |
| Failure_NetworkConfig_HarvestBeneficiaryPercentage_Exceeds_One_Hundred | Validation failed because of harvest beneficiary more than 100%. |
| Failure_NetworkConfig_MaxMosaicAtomicUnits_Invalid | Validation failed because the max mosaic amount units is invelid. |
| Failure_NetworkConfig_ApplyHeightDelta_Zero | Validation failed because the height delta is zero. |
| Failure_LockHash_Invalid_Mosaic_Id |	Validation failed because the lock does not allow the specified mosaic. The only mosaic allowed is `xpx`. |
| Failure_LockHash_Invalid_Mosaic_Amount |	Validation failed because the lock does not allow the specified amount. The minimum amount is `10`. |
| Failure_LockHash_Hash_Exists |	Validation failed because the hash is already present in cache. |
| Failure_LockHash_Hash_Does_Not_Exist |	Validation failed because the hash is not present in cache. Remember to lock before announcing aggregate bonded transactions. |
| Failure_LockHash_Inactive_Hash |	Validation failed because the hash is inactive. |
| Failure_LockHash_Invalid_Duration |	Validation failed because the duration is too long. Duration is allowed to lie up to `2` days. |
| Failure_LockHash_Plugin_Config_Malformed | Validation failed because the lockhash plugin configuration is malformed. |
| Failure_LockSecret_Invalid_Hash_Algorithm |	Validation failed because the hash algorithm for lock type secret is invalid. See the [available algorithms](../built-in-features/cross-chain-swaps.md) list. |
| Failure_LockSecret_Hash_Exists |	Validation failed because the hash is already present in cache. |
| Failure_LockSecret_Hash_Not_Implemented |	Validation failed because the hash is not implemented yet. |
| Failure_LockSecret_Proof_Size_Out_Of_Bounds |	Validation failed because the proof is too small or too large. It should be between `10` and `1000` bytes. |
| Failure_LockSecret_Secret_Mismatch |	Validation failed because the secret does not match proof. |
| Failure_LockSecret_Unknown_Composite_Key |	Validation failed because the secret is unknown. |
| Failure_LockSecret_Inactive_Secret |	Validation failed because the secret is inactive. |
| Failure_LockSecret_Hash_Algorithm_Mismatch |	Validation failed because the hash algorithm does not match. |
| Failure_LockSecret_Invalid_Duration |	Validation failed because the duration is too long. Duration is allowed to lie up to `30` days. |
| Failure_LockSecret_Plugin_Config_Malformed | Validation failed because the locksecret plugin configuration is malformed. |
| Failure_Metadata_Invalid_Metadata_Type | Validation failed because the metadata type is invalid. |
| Failure_Metadata_Modification_Type_Invalid | Validation failed because a modification type is invalid. |
| Failure_Metadata_Modification_Key_Invalid | Validation failed because a key has wrong size. |
| Failure_Metadata_Modification_Value_Invalid | Validation failed because a modification value is invalid. |
| Failure_Metadata_Modification_Key_Redundant | Validation failed because a key already exists. |
| Failure_Metadata_Modification_Value_Redundant | Validation failed because there is already modification with the same key and value. |
| Failure_Metadata_Remove_Not_Existing_Key | Validation failed because of an attempt to remove not existing key. |
| Failure_Metadata_Address_Modification_Not_Permitted | Validation failed because a modification of address is not permitted. |
| Failure_Metadata_Mosaic_Modification_Not_Permitted | Validation failed because a modification of mosaic is not permitted. |
| Failure_Metadata_Namespace_Modification_Not_Permitted | Validation failed because a modification of namespace is not permitted. |
| Failure_Metadata_Address_Not_Found | Validation failed because address is not found. |
| Failure_Metadata_Mosaic_Not_Found | Validation failed because mosaic is not found. |
| Failure_Metadata_Namespace_Not_Found | Validation failed because namespace is not found. |
| Failure_Metadata_Too_Much_Keys | Validation failed because the number of keys exceeded the limit. |
| Failure_Metadata_Plugin_Config_Malformed | Validation failed because the metadata plugin configuration is malformed. |
| Failure_Metadata_MosaicId_Malformed | Validation failed because the mosaic id is malformed. |
| Failure_Metadata_NamespaceId_Malformed | Validation failed because the namespace id is malformed. |
| Failure_Mosaic_Invalid_Duration |	Validation failed because the duration has an invalid value. Duration is allowed to lie up to `365` days. |
| Failure_Mosaic_Invalid_Name |	Validation failed because the name is invalid. The mosaic name may have a maximum length of `64` characters. Allowed characters are a-to-z; 0-to-9 and the following special characters: `_- |
| Failure_Mosaic_Name_Id_Mismatch |	Validation failed because the name and id don’t match. |
| Failure_Mosaic_Expired |	Validation failed because the parent is expired. |
| Failure_Mosaic_Owner_Conflict |	Validation failed because the parent owner conflicts with the child owner. |
| Failure_Mosaic_Id_Mismatch |	Validation failed because the id is not the expected id generated from signer and nonce. |
| Failure_Mosaic_Parent_Id_Conflict |	Validation failed because the existing parent id does not match the supplied parent id. |
| Failure_Mosaic_Invalid_Property |	Validation failed because a mosaic property is invalid. |
| Failure_Mosaic_Invalid_Flags |	Validation failed because the mosaic flags are invalid. |
| Failure_Mosaic_Invalid_Divisibility |	Validation failed because the mosaic divisibility is invalid. The specified divisibility is greater than `6` or negative. |
Failure_Mosaic_Invalid_Supply_Change_Direction |	Validation failed because the mosaic supply change direction is invalid: decrease (0) and increase (1). |
| Failure_Mosaic_Invalid_Supply_Change_Amount |	Validation failed because the mosaic supply change amount is invalid. |
| Failure_Mosaic_Invalid_Id |	Validation failed because the mosaic id is invalid. |
| Failure_Mosaic_Modification_Disallowed |	Validation failed because mosaic modification is not allowed. |
| Failure_Mosaic_Modification_No_Changes |	Validation failed because mosaic modification would not result in any changes. |
| Failure_Mosaic_Supply_Immutable |	Validation failed because the mosaic supply is immutable. |
| Failure_Mosaic_Supply_Negative |	Validation failed because the resulting mosaic supply is negative. |
| Failure_Mosaic_Supply_Exceeded |	Validation failed because the resulting mosaic supply exceeds the maximum allowed value. The range should be between 0 and `9.000.000.000`. |
| Failure_Mosaic_Non_Transferable |	Validation failed because the mosaic is not transferable. Only the creator of the mosaic is eligible to be the recipient of a non-transferable mosaic once transferred. |
| Failure_Mosaic_Max_Mosaics_Exceeded |	Validation failed because the credit of the mosaic would exceed the maximum different mosaics an account is allowed to own. Set by default to `10.000` different mosaics per account. |
| Failure_Mosaic_Plugin_Config_Malformed |	Validation failed because the mosaic plugin configuration is malformed. |
| Failure_Multisig_Modify_Account_In_Both_Sets |	Validation failed because an account is specified to be both added and removed. |
| Failure_Multisig_Modify_Multiple_Deletes |	Validation failed because there are multiple removals. |
| Failure_Multisig_Modify_Redundant_Modifications |	Validation failed because tehre are redundant modifications. |
| Failure_Multisig_Modify_Unknown_Multisig_Account |	Validation failed because account is not in multisig cache. |
| Failure_Multisig_Modify_Not_A_Cosigner |	Validation failed because there is not account to be removed. |
| Failure_Multisig_Modify_Already_A_Cosigner |	Validation failed because the account to be added is already a cosignatory. |
| Failure_Multisig_Modify_Min_Setting_Out_Of_Range |	Validation failed because thenew minimum settings are out of range. |
| Failure_Multisig_Modify_Min_Setting_Larger_Than_Num_Cosignatories |	Validation failed because min settings are larger than number of cosignatories.|
| Failure_Multisig_Modify_Unsupported_Modification_Type |	Validation failed because the modification type is unsupported: add (0) and remove (1).|
| Failure_Multisig_Modify_Max_Cosigned_Accounts |	Validation failed because the cosignatory already cosigns the maximum number of accounts. An account cannot be cosignatory of more than `5` multisig accounts. |
| Failure_Multisig_Modify_Max_Cosigners |	Validation failed because the multisig account already has the maximum number of cosignatories. A multisig account cannot have more than `10` cosignatories. |
|Failure_Multisig_Modify_Loop |	Validation failed because a multisig loop is created. A multisig account cannot be cosignatory of itself. Neither an account can be turned into multisig having as cosignatory another multisig where the account is cosignatory. |
|Failure_Multisig_Modify_Max_Multisig_Depth |	Validation failed because the max multisig depth is exceeded. The maximum depth of a multilevel multisig account is `3`. |
|Failure_Multisig_Operation_Not_Permitted_By_Account |	Validation failed because an operation is not permitted by a multisig account. A multisig account cannot be converted into a multisig account again. |
|Failure_Multisig_Plugin_Config_Malformed |	Validation failed because the multisig plugin configuration is malformed.
|Failure_Namespace_Invalid_Duration |	Validation failed because the duration has an invalid value. Duration is allowed to lie up to `365` days.
|Failure_Namespace_Invalid_Name |	Validation failed because the namespace has an invalid name. The namespace name may have a maximum length of `64` characters. Allowed characters are a-to-z; 0-to-9 and the following special characters: `_- |
|Failure_Namespace_Name_Id_Mismatch |	Validation failed because the name and id don’t match. |
|Failure_Namespace_Expired |	Validation failed because the namespace has expired. |
|Failure_Namespace_Owner_Conflict |	Validation failed because the parent owner conflicts with the child owner. |
|Failure_Namespace_Id_Mismatch |	Validation failed because the id is not the expected id generated from signer and nonce. |
|Failure_Namespace_Invalid_Namespace_Type |	Validation failed because the namespace type is invalid: rootnamespace (0) and subnamesapce (1). |
|Failure_Namespace_Root_Name_Reserved |	Validation failed because the root namespace has a [reserved name](https://github.com/proximax-storage/cpp-xpx-chain/blob/master/resources/config-network.properties#L60). |
|Failure_Namespace_Too_Deep |	Validation failed because the resulting namespace would exceed the maximum allowed namespace depth. Namespaces can have up to `3` nested levels. |
|Failure_Namespace_Parent_Unknown |	Validation failed because the namespace parent is unknown. |
|Failure_Namespace_Already_Exists |	Validation failed because the namespace already exists. |
|Failure_Namespace_Already_Active |	Validation failed because the namespace is already active. |
|Failure_Namespace_Eternal_After_Nemesis_Block |	Validation failed because an eternal namespace was received after the nemesis block. |
|Failure_Namespace_Max_Children_Exceeded |	Validation failed because the maximum number of children for a root namespace was exceeded. |
|Failure_Namespace_Alias_Invalid_Action |	Validation failed because alias action is invalid: link (0) and unlink (1). |
|Failure_Namespace_Alias_Namespace_Unknown |	Validation failed because the namespace does not exist. |
|Failure_Namespace_Alias_Already_Exists |	Validation failed because the namespace is already linked to an alias. |
|Failure_Namespace_Alias_Does_Not_Exist |	Validation failed because the namespace is not linked to an alias. |
|Failure_Namespace_Alias_Owner_Conflict |	Validation failed because the namespace has different owner. |
|Failure_Namespace_Alias_Unlink_Type_Inconsistency |	Validation failed because unlink type is not consistent with the existing alias. |
|Failure_Namespace_Alias_Unlink_Data_Inconsistency |	Validation failed because unlink data is not consistent with the existing alias. |
|Failure_Namespace_Alias_Invalid_Address |	Validation failed because the aliased address is invalid. |
|Failure_Namespace_Plugin_Config_Malformed |	Validation failed because the namespace plugin configuration is malformed. |
|Failure_Property_Invalid_Property_Type |	Validation failed because the property type is invalid. |
|Failure_Property_Modification_Type_Invalid |	Validation failed because a modification type is invalid. |
|Failure_Property_Modification_Address_Invalid |	Validation failed because a modification address is invalid. |
|Failure_Property_Modification_Operation_Type_Incompatible |	Validation failed because the operation type is incompatible. |
|Failure_Property_Modify_Unsupported_Modification_Type |	Validation failed because the modification type is unsupported: add (0) and delete (1). |
|Failure_Property_Modification_Redundant |	Validation failed because a modification is redundant. |
|Failure_Property_Modification_Not_Allowed |	Validation failed because there is not a value in the container. |
|Failure_Property_Modification_Count_Exceeded |	Validation failed because the transaction has too many modifications. |
|Failure_Property_Values_Count_Exceeded |	Validation failed because the resulting property has too many values. The maximum number of values a property can have is `512`. |
|Failure_Property_Value_Invalid |	Validation failed because the property value is invalid. |
|Failure_Property_Signer_Address_Interaction_Not_Allowed |	Validation failed because the signer is not allowed to interact with an address involved in the transaction. |
|Failure_Property_Mosaic_Transfer_Not_Allowed |	Validation failed because the mosaic transfer is prohibited by the recipient. |
|Failure_Property_Transaction_Type_Not_Allowed |	Validation failed because the transaction type is not allowed to be initiated by the signer. |
|Failure_Property_Plugin_Config_Malformed | Validation failed because the property plugin configuration is malformed. |
|Failure_Service_Drive_Duration_Is_Not_Multiple_Of_BillingPeriod | Validation failed because the duration multiple of is not billing period. |
|Failure_Service_Wrong_Percent_Approvers | Validation failed because the percentage of approvers is wrong. |
|Failure_Service_Min_Replicators_More_Than_Replicas | Validation failed because the minimum number of replicates more than the number of replicas. |
|Failure_Service_Drive_Invalid_Duration | Validation failed because the duration is invalid. |
|Failure_Service_Drive_Invalid_Billing_Period | Validation failed because the billing period is invalid. |
|Failure_Service_Drive_Invalid_Billing_Price | Validation failed because the billing price is invalid. |
|Failure_Service_Drive_Invalid_Size | Validation failed because the size is invalid. |
|Failure_Service_Drive_Invalid_Replicas | Validation failed because the number of replicas is invalid. |
|Failure_Service_Drive_Invalid_Min_Replicators | Validation failed because the minimum number of replicas is invalid. |
|Failure_Service_Drive_Already_Exists | Validation failed because the drive with this id already exists. |
|Failure_Service_Plugin_Config_Malformed | Validation failed because the service plugin configuration is malformed. |
|Failure_Service_Operation_Is_Not_Permitted | Validation failed because the operation is not permitted. |
|Failure_Service_Drive_Does_Not_Exist | Validation failed because the drive with this id does not exists. |
|Failure_Service_Replicator_Already_Connected_To_Drive | Validation failed because the replicator already connected to this drive. |
|Failure_Service_Root_Hash_Is_Not_Equal | Validation failed because the root hash is not equal. |
|Failure_Service_File_Hash_Redundant | Validation failed because the file hash is redundant. |
|Failure_Service_File_Doesnt_Exist | Validation failed because the file does not exist. |
|Failure_Service_Too_Many_Files_On_Drive | Validation failed because the drive is full. |
|Failure_Service_Drive_Replicator_Not_Registered | Validation failed because the replicator is not registered. |
|Failure_Service_Drive_Root_No_Changes | Validation failed because the root hash has not changed. |
|Failure_Service_Drive_Has_Ended | Validation failed because the drive duration is expired. |
|Failure_Service_Drive_Cant_Find_Default_Exchange_Offer | Validation failed because default exchange offer not found. |
|Failure_Service_Exchange_Of_This_Mosaic_Is_Not_Allowed | Validation failed because the exchange of this mosaic is not allowed. |
|Failure_Service_Drive_Not_In_Pending_State | Validation failed because the drive is not in the pending state. |
|Failure_Service_Exchange_More_Than_Required | Validation failed because the sum of the exchange more than is required. |
|Failure_Service_Exchange_Cost_Is_Worse_Than_Default | Validation failed because the exchange cost is worse than the default offer one. |
|Failure_Service_Drive_Processed_Full_Duration | Validation failed because the drive duration is expired. |
|Failure_Service_Zero_Upload_Info | Validation failed because there is no upload info. |
|Failure_Service_Participant_Redundant | Validation failed because the participant is redundant. |
|Failure_Service_Participant_Is_Not_Registered_To_Drive | Validation failed because the participant is not registered to the drive. |
|Failure_Service_Zero_Deleted_Files | Validation failed because there are zero deleted files. |
|Failure_Service_Zero_Infos | Validation failed because there is no info. |
|Failure_Service_File_Deposit_Is_Zero | Validation failed because no deposit is zero. |
|Failure_Service_Verification_Already_In_Progress | Validation failed because of the verification already in progress.. |
|Failure_Service_Verification_Has_Not_Started | Validation failed because of the verification has not started. |
|Failure_Service_Verification_Is_Not_Active | Validation failed because of the verification is not active. |
|Failure_Service_Verification_Has_Not_Timed_Out | Validation failed because of the verification has not timed out. |
|Failure_Service_Drive_Is_Not_In_Progress | Validation failed because the drive is not in the progress state. |
|Failure_Service_Replicator_Has_Active_File_Without_Deposit | Validation failed because the replicator has an active file without deposit. |
|Failure_Service_Remove_Files_Not_Same_File_Size | Validation failed because the removing files have a different file size. |
|Failure_Service_Doesnt_Contain_Streaming_Tokens | Validation failed because it does not contain streaming tokens. |
|Failure_Service_Drive_Size_Exceeded | Validation failed because the drive size is exceeded. |
|Failure_Service_Failed_Block_Hashes_Missing | Validation failed because block hashes are missing. |
|Failure_Service_Duplicate_Failed_Block_Hashes | Validation failed because block hashes are duplicated. |
|Failure_Transfer_Message_Too_Large |	Validation failed because the message is too large. It exceeds the limit of `1024` bytes. |
|Failure_Transfer_Out_Of_Order_Mosaics |	Validation failed because the mosaics are out of order. Mosaics on a transfer transaction should be ordered by id value. |
| Failure_Transfer_Plugin_Config_Malformed |	Validation failed because the transfer plugin configuration is malformed. |
| Failure_Transfer_Too_Many_Mosaics | Validation failed because there are too many mosaics. |
| Failure_Transfer_Zero_Amount | Validation failed because there is zero amount of mosaics. |
| Failure_BlockChainUpgrade_Invalid_Signer | Validation failed because the blockchain upgrade transaction signer is not nemesis account. |
| Failure_BlockChainUpgrade_Upgrade_Period_Too_Low | Validation failed because the blockchain upgrade period is too low. |
| Failure_BlockChainUpgrade_Redundant | Validation failed because a blockchain upgrade has already been set up at the height. |
| Failure_BlockChainUpgrade_Invalid_Current_Version | Validation failed because the current blockchain version is invalid. |
| Failure_BlockChainUpgrade_Plugin_Config_Malformed | Validation failed because the blockchain upgrade plugin configuration is malformed. |
| Failure_BlockChainUpgrade_Version_Lower_Than_Current | Validation failed because the blockchain version is lower than the current one. |
| Failure_Chain_Unlinked |	Validation failed because a block was received that did not link with the existing chain. |
| Failure_Chain_Block_Not_Hit |	Validation failed because a block was received that is not a hit. |
| Failure_Chain_Block_Inconsistent_State_Hash |	Validation failed because a block was received that has an inconsistent state hash. |
| Failure_Chain_Block_Inconsistent_Receipts_Hash |	Validation failed because a block was received that has an inconsistent receipts hash. |
| Failure_Chain_Unconfirmed_Cache_Too_Full |	Validation failed because the unconfirmed cache is too full. |
| Failure_Consumer_Empty_Input |	Validation failed because the consumer input is empty. |
| Failure_Consumer_Block_Transactions_Hash_Mismatch |	Validation failed because the block transactions hash does not match the calculated value. |
| Failure_Consumer_Hash_In_Recency_Cache |	Validation failed because the entity hash is present in the recency cache. |
| Failure_Consumer_Remote_Chain_Too_Many_Blocks |	Validation failed because the chain part has too many blocks. |
| Failure_Consumer_Remote_Chain_Improper_Link |	Validation failed because the chain is internally improperly linked. |
| Failure_Consumer_Remote_Chain_Duplicate_Transactions |	Validation failed because the chain part contains duplicate transactions. |
| Failure_Consumer_Remote_Chain_Unlinked |	Validation failed because the chain part does not link to the current chain. |
| Failure_Consumer_Remote_Chain_Mismatched_Difficulties |	Validation failed because the remote chain difficulties do not match the calculated difficulties.|
| Failure_Consumer_Remote_Chain_Score_Not_Better |	Validation failed because the remote chain score is not better. |
| Failure_Consumer_Remote_Chain_Too_Far_Behind |	Validation failed because the remote chain is too far behind. |
| Failure_Consumer_Remote_Chain_Too_Far_In_Future |	Validation failed because the remote chain timestamp is too far in the future. |
| Failure_Extension_Partial_Transaction_Cache_Prune |	Validation failed because the partial transaction was pruned from the temporal cache. |
| Failure_Extension_Partial_Transaction_Dependency_Removed |	Validation failed because the partial transaction was pruned from the temporal cache due to its dependency being removed. |
| Failure_Exchange_Offer_Doesnt_Exist | Validation failed because the offer does not exist. |
| Failure_Exchange_Zero_Amount | Validation failed because the amount is zero. |
| Failure_Exchange_Zero_Price | Validation failed because the price is zero. |
| Failure_Exchange_No_Offers | Validation failed because there are no offers. |
| Failure_Exchange_Mosaic_Not_Allowed | Validation failed because mosaic is not allowed. |
| Failure_Exchange_Buying_Own_Units_Is_Not_Allowed | Validation failed because there is no possibility of buying own units. |
| Failure_Exchange_Not_Enough_Units_In_Offer | Validation failed because of not enough units in the offer. |
| Failure_Exchange_Invalid_Price | Validation failed because of the price is invalid. |
| Failure_Exchange_Account_Doesnt_Have_Any_Offer | Validation failed because the account does not have any offers. |
| Failure_Exchange_Offer_Duration_Too_Large | Validation failed because the offer duration is too large. |
| Failure_Exchange_Plugin_Config_Malformed | Validation failed because the exchange plugin configuration is malformed. |
| Failure_Exchange_No_Offered_Mosaics_To_Remove | Validation failed because there are no offered mosaics to remove. |
| Failure_Exchange_Duplicated_Offer_In_Request | Validation failed because the offer is duplicated in the request. |
| Failure_Exchange_Offer_Exists | Validation failed because the offer already exists. |
| Failure_Exchange_Zero_Offer_Duration | Validation failed because the offer duration is zero. |