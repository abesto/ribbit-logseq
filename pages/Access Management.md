public:: true

- Access control is always a balance between convenience and security. Given our [[Threat Model]] we may want to err more on the side of security.
- In [[Central Infrastructure Security]], this might just be following best practices.
	- Require 2FA on all relevant accounts
	- Ensure only trusted parties have access to infrastructure components
		- Maintain a list of access grants so that they can be quickly and efficiently (maybe automatically) revoked if trust is lost
	- Special care should be given to source code repository write access, database write / admin access, and fleet management admin access
- In [[Device Security]] the big question is: what level of access should the device owner have to the device?
	- In principle, I'd expect to have full access to a device running in my home. But also, device owners shouldn't be able to, either maliciously or accidentally, poison the data collected by the device - see [[Data Provenance]]
	- By default and in general, we should assume ((62dd66f0-1d6e-4bef-8548-a3e85a8ecc1d)) can gain physical access to any given sensor. This means physical access should NOT be enough to modify the running code. How do we achieve that? I don't know off the top of my head :D
	- ((62dd74c6-7d82-457e-ab4e-ebb43d9ba37a))