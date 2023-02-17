# Compounding

USDC locked in the zkBob contract can be allocated to Aave to earn interest and AAVE tokens. The yield from this allocation can then be used to support the BOB protocol.

The contract interacts directly with the Aave lending platform to provide a seamless user experience. When a user swaps BOB for USDC, the USDC is withdrawn automatically from Aave and returned to the user. Generated yield from Aave is collected periodically from the protocol.

Basic compounding functionality is already built into the application and is currently in beta operation.
