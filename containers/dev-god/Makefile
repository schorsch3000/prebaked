.PHONY: precommit

precommit:
	rm -rf -- packages.*
	find ../ -type f -name packages.apt -exec awk 1 "{}" + | sort | uniq | sponge packages.apt
	find ../ -type f -name packages.pipx -exec awk 1 "{}" + | sort | uniq | sponge packages.pipx
